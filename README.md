# TDD

- [Montando cenários de testes com o Pytest](https://www.alura.com.br/artigos/montando-cenarios-de-testes-com-o-pytest?_gl=1*9mz9pa*_ga*MzY5ODE4OTMyLjE2ODE3NjU1NjY.*_ga_1EPWSW3PCS*MTY5MzA3NDkyNS4yNC4xLjE2OTMwNzcxMDMuMC4wLjA.*_fplc*bVE3cFNINW1CcnhpQU1ld3YlMkZrSU1UR0hxbSUyQllxYXNaZEdTazV2WlVsb2VqS0c0UmFtNmJ4T2NSUEo4aEZLemdSWGxneHVMcENyVSUyQnlWUHQ3VGpRdiUyQkpPaU1LM0Q3dWc0aVlmNTIwZmRCU2xXYjlXZXBab1JMcTVEUDhVeUElM0QlM0Q.*_ga_59FP0KYKSM*MTY5MzA3NDkyNS4xNjUuMS4xNjkzMDc3MTAzLjAuMC4w)

## Ambiente virtual

```bash
    python3 -m venv venv
    source venv/bin/activate
```

## Instalação de pacotes

```bash
    pip install pytest==7.1.2
    pip freeze > requirements.txt # gerar informações de tudo que estamos instalando
```

## Metodologia Given-When-Then

- Dado `Contexto:` entrada
- Quando `Ação:` chamada de método
- Então `Desfecho:` verificação se **resultado** é igual ao **esperado**

## Pytest

```bash
    pytest -v # verboso

    pytest --cov # coverage
    pytest --cov=codigo tests/ #diretorio
    pytest --cov=codigo tests/ --cov-report term-missing # report no terminal
    pytest --cov=codigo tests/ --cov-report html # report html
    pytest --junitxml report.xml # report xml
    pytest --cov-report xml # report coverage xml
```

## Markers

- [documentação](https://docs.pytest.org/en/7.1.x/how-to/mark.html#mark)

```bash
    # @mark.calcular_bonus
    pytest -v -m calcular_bonus
```

```python
    @pytest.mark.skip(reason="não quero executar isso agora")
    def test_aleatorio():
        ...

    import sys

    @pytest.mark.skipif(sys.version_info < (3, 10), reason="Requer Python na versão 3.10 ou superior")
    def test_funcao():
        ...

    @pytest.mark.xfail
    def test_funcao():
        ...
```

## pytest.ini

Sempre que executamos o Pytest no terminal/prompt de comando, ele procura as configurações que deve seguir para a execução dos testes.

**O arquivo pytest.ini possibilita alterações nas configurações padrão do Pytest.**

- [documentação](https://docs.pytest.org/en/7.1.x/reference/reference.html#ini-options-ref)

`Exemplo`

```bash
    [pytest]
    python_functions=*_testando
    python_classes=testando_*
    python_files=muitos_testes_*
```
