.PHONY: lint
lint: #lints the package for common code smells
	which golangci-lint || sh boilerplate/lyft/golang_test_targets/golangci-lint.sh -b $$GOPATH/bin v1.51.2
	golangci-lint run --timeout 5m

# If code is failing goimports linter, this will fix.
# skips 'vendor'
.PHONY: goimports
goimports:
	@boilerplate/lyft/golang_test_targets/goimports

.PHONY: test_unit
test_unit:
	go test -cover ./... -race

.PHONY: test_benchmark
test_benchmark:
	go test -bench . ./...

.PHONY: test_unit_cover
test_unit_cover:
	go test ./... -coverprofile /tmp/cover.out -covermode=count; go tool cover -func /tmp/cover.out

.PHONY: test_unit_visual
test_unit_visual:
	go test ./... -coverprofile /tmp/cover.out -covermode=count; go tool cover -html=/tmp/cover.out
