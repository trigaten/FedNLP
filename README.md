# FedNLP

Code and Data for **GPT Deciphering Fedspeak: Quantifying Dissent Among Hawks and Doves**, a paper published at Findings of EMNLP 2023.

## Setup

This section shows you how to setup your codebase and OpenAI key in order to run code in this repository.

1. Run `pip install -r requirements.txt`
2. Create a .env file at root level (same level as this README) and put in it `OPENAI_KEY=sk-REST_OF_KEY`. Replace `sk-REST_OF_KEY` with your actual OpenAI API key.

## Data

`results/statements_scores` is generated by 0-shot prompting GPT-4 to label each statement as one of ("dovish", "mostly dovish", "neutral", "mostly hawkish", "hawkish")

`results/minutes_scores` is generated by 0-shot prompting GPT-4 to label each minutes file as one of ("dovish", "mostly dovish", "neutral", "mostly hawkish", "hawkish")

`results/statements_scores_by_sentence.json` is generated by 0-shot prompting GPT-4 to label each sentence of each statement as one of ("dovish", "mostly dovish", "neutral", "mostly hawkish", "hawkish")

`None` means that GPT-4 did not return one of the five labels. `"TOO SHORT"` means that the sentence was less than 5 characters, and was thus not analyzed.

`results/transcripts_full_score.json` is generated by 0-shot prompting GPT-4-32K to examine all of each speakers speech, and provide each speaker a single score for each transcript, one of ("dovish", "mostly dovish", "neutral", "mostly hawkish", "hawkish").

`results/statements_scores_by_sentence_few_shot` is generated by few-shot prompting GPT-4 to examine sentences in each statement, score each sentence as one of ("dovish", "mostly dovish", "neutral", "mostly hawkish", "hawkish"). `Null` means the sentence did not properly receive a label.

## Citation

```bibtex
@article{peskoff2023gpt,
  title={Deciphering Fedspeak: Quantifying Dissent Among Hawks and Doves},
  author={Peskoff, Denis and Visokay, Adam and Schulhoff, Sander V and Wachspress, Benjamin and Blinder, Alan and Stewart, Brandon M},
  journal={Findings of EMNLP},
  volume={2023},
  year={2023},
  month={October},
  day={20},
  keywords={FOMC, Fed, GPT, LLM},
  abstract={Markets and policymakers around the world hang on the consequential monetary policy decisions made by the Federal Open Market Committee (FOMC). Publicly available textual documentation of their meetings provide insight into members' attitudes about the economy. We use GPT-4 to quantify dissent among members on the topic of inflation. We find that transcripts and minutes reflect the diversity of member views about the macroeconomic outlook in a way that is lost or omitted from the public statements. In fact, diverging opinions that shed light upon the committee's "true" attitudes are almost entirely omitted from the final statements. Hence, we argue that forecasting FOMC sentiment based solely on statements will not sufficiently reflect dissent among the hawks and doves.},
  type={Regular Short Paper},
  track={NLP Applications},
  track2={Computational Social Science and Cultural Analytics},
}
```
