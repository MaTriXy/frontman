.DEFAULT_GOAL := help
.PHONY: help build test test-watch lint format clean publish

help: ## Display this help message
	@awk 'BEGIN {FS = ":.*##"} /^[a-zA-Z_-]+:.*##/ { printf "  %-15s %s\n", $$1, $$2 }' $(MAKEFILE_LIST)

build: ## Build ReScript + bundle with tsup
	yarn build

publish: build ## Build and publish to npm (pass OTP=<code> for 2FA)
	npm publish $(if $(OTP),--otp=$(OTP))

test: ## Run tests
	yarn build:rescript
	yarn vitest run

test-watch: ## Run tests in watch mode
	yarn vitest

lint: ## Check formatting
	yarn rescript format -check src

format: ## Format code
	yarn rescript format src

clean: ## Clean build artifacts
	yarn rescript clean
	rm -rf dist
