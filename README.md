[![Spring Boot Checkstyle](https://github.com/danielso2007/spring-boot-checkstyle/actions/workflows/maven.yml/badge.svg)](https://github.com/danielso2007/spring-boot-checkstyle/actions/workflows/maven.yml)

# Visão Geral

Checkstyle é uma ferramenta de código aberto que verifica o código em relação a um conjunto configurável de regras. Checkstyle é uma ferramenta de desenvolvimento para ajudar programadores a escrever código Java que segue um padrão de codificação. Ele automatiza o processo de verificação do código Java para poupar os desenvolvedores dessa tarefa chata (mas importante). Isso o torna ideal para projetos que desejam impor um padrão de codificação.

# Funcionamento

Checkstyle pode verificar muitos aspectos do seu código-fonte. Ele pode encontrar problemas de design de classe, problemas de design de método. Ele também tem a capacidade de verificar o layout do código e problemas de formatação.

# Qual a importância de aplicar code style?

A maior parte do tempo de vida de um software não é no desenvolvimento, mas em manutenção, como correção de bugs e melhorias. Outro fato importante é que dificilmente quem desenvolveu o software ficará responsável por sua manutenção durante todo o tempo que ele estiver em operação. Quanto mais fácil de ler e compreender seu código, menos tempo um desenvolvedor levará para conseguir se integrar à equipe.

Portanto, aplicar o code style é uma ação simples que reduz o "atrito" e contribui muito para a saúde do projeto.

# Plugin Maven Checkstyle

## Configuração do Maven

Para adicionar Checkstyle a um projeto, precisamos adicionar o plugin na seção de build do `pom.xml`:

### Properties do maven:

```xml
<maven-checkstyle-plugin-version>3.2.0</maven-checkstyle-plugin-version>
<local-config-checkstyle>config/checkstyle.xml</local-config-checkstyle>
```

### Plugin:

```xml
<plugins>
…
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>${maven-checkstyle-plugin-version}</version>
    <configuration>
        <configLocation>${local-config-checkstyle}</configLocation>
    </configuration>
    <executions>
        <execution>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
</plugin>
…
</plugins>
```

Este plug-in vem com duas verificações predefinidas, uma verificação no estilo Sun e uma verificação no estilo Google. A verificação padrão para um projeto é `sun_checks.xml`.

Para usar uma configuração personalizada, podemos especificar o arquivo de configuração conforme mostrado no exemplo acima. Usando esta configuração, o plug-in agora lerá a configuração personalizada em vez da configuração padrão.

A versão mais recente do plugin pode ser encontrada no [Maven Central](https://mvnrepository.com/artifact/org.apache.maven.plugins/maven-site-plugin/3.12.1).

# Arquivo checkstyle padrão

Para os projetos, usaremos este `checkstyle.xml`.

Verificando o código da aplicação

Configurando o `<goal>check</goal>`, a verificação de objetivo mencionada na seção de executions solicita que o plug-in seja executado na fase de verificação da compilação e força uma falha de compilação quando ocorre uma violação dos padrões de codificação.

Agora, se executarmos o comando `./mvnw clean install`, ele verificará os arquivos em busca de violações e a compilação falhará se alguma violação for encontrada.

Também podemos executar apenas o objetivo de verificação do plugin usando `./mvnw checkstyle:check`. A execução desta etapa também resultará em uma falha de compilação se houver algum erro de validação.

O comando `./mvnw clean verify` também pode ser executado para verificar violação dos padrões de codificação.

# Projeto

Casos queira rodar o projeto, execute `./mvnw spring-boot:run`.

# Formatação padrão do código usando a IDE

Para a formatação do código usando um padrão, configure a IDE usando os arquivos `clean_up.xml` e `formatter.xml` conforme abaixo:

## Formatter

- Na IDE, acesse o menu `Window -> Preferences`
- Depois acesse `Java -> Code Style -> Formatter`
- Clique no botão `Import…`
- Selecione o arquivo `formatter.xml`
- Após importar, selecione o `Active profile: Formatter-Padrão`

Depois, na sua classe java, execute `ctrl+shift+F`. Neste momento seu código será formatado com o padrão do XML importado.

## Clean Up

Clean Up é uma ferramenta que a IDE Eclipse dispõe para realizar a limpeza de seu código Java. Isso é muito útil para auxiliar em padrões de codificação dentro de uma equipe de desenvolvimento, onde cada um seguirá o mesmo padrão definido automaticamente.

Para o fonte, usando o clean-up, seguir os passos:

- Na IDE, acesse o menu `Window -> Preferences`
- Depois acesse `Java -> Code Style -> clean Up`
- Clique no botão `Import…`
- Selecione o arquivo `clean_up.xml`
- Após importar, selecione o `Active profile: Clean-Up-Padrão`

# Conclusão

Usando o clean up e o formatter, o código estará quase 100% preparado e padronizado, precisando de poucas modificações no código. Antes de formatar (também com clean up) todo um projeto, verifique se todos os testes contemplam todos os cenários necessários para uma grande refatoração.




