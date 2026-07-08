testes = 1 2 3 4 5 6 7 8 9 10

all: exec test

test: exec
	@ echo "Criando diretório para saídas..."
	@ mkdir -p tests

	@ echo "Testando..."
	@ echo "Sua saída: <	Output: >"
	@ $(foreach i, $(testes), ./exec < in/input$(i).txt > tests/out$(i).txt;)
	@ $(foreach i, $(testes), echo "Teste $(i)" && diff tests/out$(i).txt out/output$(i).txt;)

exec: T02.c
	@ echo "Compilando o arquivo..."
	@ gcc $< -o $@

clean:
	@ rm -rf tests
	@ rm -f exec