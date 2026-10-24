# Contributing

Thanks for helping keep these guides accurate — cloud certifications change every few months.

## Report a problem

Open an issue with the **Outdated or wrong content** template and include a link to the official documentation.

## Fix it yourself

1. Fork the repository and edit the Markdown guide or the trainer file.
2. In a trainer (`*-trainer.html`), questions live in the `const Q = [ ... ]` array. Each question has:
   - `id`, `d` (domain number), `s` (skill), `t` (type: `single`, `multi`, `drop`, `yesno`, `order`)
   - `q` (question), the options/answers for its type, `x` (explanation) and `r` (official source).
3. Explanations should say **why each wrong option is wrong**, not only why the right one is right.
4. Open the trainer in your browser and answer your new question once before submitting.
5. Open a pull request describing the change and its source.

## Rules

- **No real exam questions or "dumps".** They are protected by the certification providers' agreements. Write original questions based on the public skills outlines and documentation.
- Keep explanations short, factual and linked to an official source.
- By contributing, you agree that your contribution is licensed under [CC BY 4.0](LICENSE).
