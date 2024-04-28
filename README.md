
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Ollama R Library

<!-- badges: start -->
<!-- badges: end -->

The Ollama R library provides the easiest way to integrate R with
[Ollama](https://ollama.com/). For Ollama Python, see
[ollama-python](https://github.com/ollama/ollama-python).

## Installation

You can install the development version of ollamar like so:

``` r
devtools::install_github("hauselin/ollamar")
```

If it doesn’t work or you don’t have `devtools` installed, please run
`install.packages("devtools")` in R or RStudio first.

## Usage

``` r
library(ollamar)

# test connection to Ollama server
test_connection()

# list available models
list_models()
```

### Chat

``` r
messages <- list(
    list(role = "user", content = "Who is the prime minister of the uk?")
)
chat("llama3", messages)  # returns a httr2 response object
chat("llama3", messages, output = "df")
chat("llama3", messages, output = "raw")
chat("llama3", messages, output = "jsonlist")

messages <- list(
    list(role = "user", content = "Hello!"),
    list(role = "assistant", content = "Hi! How are you?"),
    list(role = "user", content = "Who is the prime minister of the uk?"),
    list(role = "assistant", content = "Rishi Sunak"),
    list(role = "user", content = "List all the previous messages.")
)
chat("llama3", messages)
```

#### Streaming responses

``` r
messages <- list(
    list(role = "user", content = "Hello!"),
    list(role = "assistant", content = "Hi! How are you?"),
    list(role = "user", content = "Who is the prime minister of the uk?"),
    list(role = "assistant", content = "Rishi Sunak"),
    list(role = "user", content = "List all the previous messages.")
)
chat("llama3", messages, stream = TRUE)
```
