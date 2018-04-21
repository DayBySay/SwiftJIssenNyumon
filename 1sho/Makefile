all:

run-hello.swift:
	swift ./hello.swift

run-args.swift:
	swift ./args.swift  args1 args2 args3

hello: hello.swift
	swiftc ./hello.swift

main: print_hello.swift main.swift
	swiftc ./print_hello.swift ./main.swift
