Uma grande tendência das statups é a criação de projetos em uma
velocidade astronômica para que os mesmos possam ser colocados no
mercado de forma serem validados. Isso sendo feito o destino dos mesmos
é definido entre uma gama de opções: descontinuado, continuado mas não
precisa de novas funcionalidades, precisa de manutenção etc.

Um problema nesse inicio de projeto é a qualidade do mesmo. Certa vez o
fundador do Likedin Reid Hoffman disse:

*Se você não tem vergonha da primeira versão do seu produto, você
demorou demais para lançar.*

Por mais que se aplique ao produto que o consumidor irá encontrar isso
não deve ser aplicado ao código, grandes customizações não são
necessárias, porém existem pequenas práticas que podem garantir uma boa
manutenção no futuro além de  economia de tempo ( nosso mais caro recurso ) e
dinheiro.

Aqui na [Codelitt](codelitt.com) a maior parte de nossos projetos são
feitos com Ruby/Rails, sendo assim definimos a utilização de um conjunto
 de gemas em todos os projetos para garantir um mínimo de
segurança e manutenibilidade:

#### Qualidade de código
##### [Rubocop](https://github.com/bbatsov/rubocop)

O Rubocop faz uma análise estática no código buscando por 'ofensas' á
boas práticas definidas pela comunidade, tails como: Complexidade
excessiva em um método, numero de linhas de uma classe, numero de
caracteres em uma linha e etc. Além de nos mostrar os problemas do
código ele nos fornece uma autocorreção simples que pode ser
customizada.

Na [Codelitt](codelitt.com) nós temos uma política de 0 warnings, no
nosso CI. Antes de fazer a build o rubocop é ativado, caso alguma ofença
seja encontrada a mesma falha antes mesmo de rodar os testes.

##### [Rubycritic](https://github.com/whitesmith/rubycritic)

O Rubycritic é outra ferramenta de análise estática, este além de
avaliar os códigos nos fornece dados como código duplicado e
complexidade.

#### Segurança

###### [Brakeman](https://github.com/presidentbeef/brakeman)

O Brakeman faz uma analise está no código buscando falhas de segurança
no mesmo, na [Codelitt](codelitt.com) nossa politica é de 0 warnings,
esse é o nosso primeiro passo na build, caso alguma brecha de segurança
seja encontrada a mesma irá falhar.

###### [Dawnscanner](https://github.com/thesp0nge/dawnscanner)

O Dawnscanner é outra gema que faz analise estática no código em busca
de falhas na segurança.

###### [Bundler-audit](https://github.com/rubysec/bundler-audit)

O bundler audit é uma gem que verifica o Gemfile.lock e busca por falhas
nas gemas utilizadas. Durante o desenvolvimento de uma aplicação é comum
que nos importemos com falhas de segurança no projeto, no entanto caso
uma gema utilizada esteja comprometida todo o projeto também estará.

#### Cobertura de código

##### [Simplecov](https://github.com/colszowka/simplecov)

O SimpleCov é uma gema que faz uma análise dinâmica da cobertura de
código, costumamos utiliza-la em conjunto com o RSpec. Além de oferecer
relatórios sobre os testes ela também permite que os mesmos falhem caso
uma porcentagem mínima não seja atingida.

Aqui na [Codelitt](codelitt.com) definimos que o mínimo de cobertura
deverá ser 90%, assim garantimos sempre que nossos projetos estejam
sendo sendo bem testados.

Vale lembrar que essa cobertura conta apenas linhas de código e não
nós, então mesmo que a cobertura esteja alta deve-se ficar atento se
todos os ramos estão sendo verificados.