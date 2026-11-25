# Benchmarking `better_profanity`

This directory provides code for benchmarking the memory usage and speed of `better_profanity`.

## Setup

Follow the **Installation** instructions for `better_profanity` to ensure the version you intend to benchmark is installed.

Install additional dependencies by running

```sh
pip install -r requirements.txt
```

## Usage

### Benchmark memory usage

To test the memory usage of a profanity filter using the default word list run

```sh
python scripts/filter_memory.py
```

To test the memory usage when using a particular word list run

```sh
python scripts/filter_memory.py <WORDLIST>
```

### Benchmark speed

To test the speed of text censoring against a dataset of paragraphs run

`````md
We are preparing to create a specification framework. Inform yourself of the work so far by reading my rough notes starting here: ⚑
My goal is to migrate my current specification draft from the Wiki into a semi-structured knowledge graph leveraging the Foam plugin in VS Code. You can also find more ideas about this in the notes.
I have years of experience with Obsidian, but I am completely new to Foam.
I've installed the plugin, started setting it up in settings.json ⚑, and created a temporary folder to experiment with at ⚑.

Current task:
1. Inform yourself of the relevant details of the Foam plugin so you know how it works and can help me interact with it inside this workspace.
2. Create a POC showcase of how the result could look like: without making any changes to the source file at ⚑, transform it into a set of interlinked notes in the Foam folder as follows:
    1. Each concept in the source glossary should have its own note. The first paragraph after the H1 heading should be the summary of what that concept is. This should equal its current glossary definition.
    2. Map the glossary definitions to the relevant headings where one exists. Move the body of the heading into that note.
    3. Headings without their own glossary definition should be extracted into separate notes if they make sense as a standalone concept, else be left inside their parent concept.
    4. Every time a concept with its own note is mentioned, a wikilink `[[name]]` should be used instead of a bare `name`.
    5. Ignore the uncommitted HTML comments in the source.
    6. In the end, we should be left with content roughly equal to the source, but organized as a knowledge graph of notes.

3. Write a script that generates a human-readable glossary to ⚑ based on these notes. Each note gets its own list entry with the name linking to the note and the description matching the first paragraph of the note as discussed before.
4. Provide a report of how you think this went, what difficulties you faced, how you think this structure would or would not be useful compared to the original.

Please get going. If there are major blockers, let me know. If you only have minor design detail questions, make the decisions yourself and proceed. This is a POC. I want to see how it would look, and then we draw conclusions at the end.
`````

Note that this script uses `pytest` and `pytest-benchmark`. If you run the command via `pytest scripts/paragraphs.py` you will have more control over the benchmarking procedures. Read up on [`pytest-benchmark`'s command-line options](https://pytest-benchmark.readthedocs.io/en/latest/usage.html#commandline-options) for more details.

## Limitations

1. Memory usage reported by `memory.py` may vary slightly between runs. Run `memory.py` several times and compute an average for a more accurate memory benchmark.
2. The dataset used by `paragraphs.py` may not be valid for all versions of `better_profanity`. If some words contained in the default word list are removed, some paragraphs' text may not be censored as expected.
