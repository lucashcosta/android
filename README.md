Biblioteca de integração PagSeguro para Android
===============================================

Descrição
---------

Versão Beta da biblioteca para plataforma Android.
A lib facilita o processo de checkout via PagSeguro dentro da plataforma Android, garantindo um fluxo de checkout transparente para o usuário final. 

OBSERVAÇÃO: Lib mock, funcionando offline ainda

Requisitos
----------

 - [Android] 2.3.+
 - [GSon]


Instalação
----------

Baixe o [último JAR][1] ou obtenha via Maven:
```xml
<repositories>
  <repository>
    <id>pagseguro-github</id>
    <name>Maven Repository PagSeguro</name>
    <layout>default</layout>
    <url>https://raw.githubusercontent.com/everton-rosario/android/mvn-repo/</url>
  </repository>
</repositories>
  
<dependency>
    <groupId>br.com.uol.ps</groupId>
    <artifactId>library</artifactId>
    <version>0.1</version>
</dependency>
```

Ou configure via Gradle:

```gradle
...
repositories {
    mavenCentral()
    mavenLocal()
    maven {
        url "https://raw.github.com/pagseguro/android/mvn-repo/"
    }
}

...

dependencies {
    ...
    compile 'br.com.uol.ps:library:0.1'
    compile 'com.google.code.gson:gson:+'
    ...
}
```

Exemplo de Uso
--------------

Permissões necessárias para a Lib funcionar.
Adicionar no Android-Manifest.xml
```xml
  <uses-permission android:name="android.permission.INTERNET" />
  <uses-permission android:name="android.permission.READ_PHONE_STATE" />
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
  <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```


Chamada de pagamento a ser adicionada:
```java
  PagSeguro.pay(new PagSeguroRequest().withAmount(BigDecimal(1.00))
                                      .withVendorEmail("suporte@lojamodelo.com.br")
                                      .withBuyerEmail("comprador@mail.com.br")
                                      .withBuyerCellphoneNumber("5511992190364")
                                      .withReferenceCode("123"),
                getActivity(),
                R.id.container,
                new PagSeguro.PagSeguroListener() {
      @Override
      public void onSuccess(PagSeguroResponse response, Context context) {
          Toast.makeText(context, "Lib PS retornou pagamento aprovado!", Toast.LENGTH_LONG).show();
      }
  
      @Override
      public void onFailure(PagSeguroResponse response, Context context) {
          Toast.makeText(context, "Lib PS retornou FALHA no pagamento!", Toast.LENGTH_LONG).show();
      }
  });
```




Executando a Loja Modelo (Exemplo)
----------------------------------

Para executar o projeto exemplo:
- Fazer clone do repositorio do github
- Importar na sua IDE (Android Studio ou Eclipse)
- Executar o modulo "app"


Dúvidas?
----------
---
Caso tenha dúvidas ou precise de suporte, acesse nosso [fórum].


Changelog
---------
0.1
 - Versão inicial com contratos de interface iniciais
 - Não existe conexão com o servidor do PagSeguro


Licença
-------

Copyright 2014 PagSeguro Internet LTDA.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.


Notas
-----

 - O PagSeguro somente aceita pagamento utilizando a moeda Real brasileiro (BRL).
 - Certifique-se que o email e o token informados estejam relacionados a uma conta que possua o perfil de vendedor ou empresarial.
 - Certifique-se que tenha definido corretamente o charset de acordo com a codificação (ISO-8859-1 ou UTF-8) do seu sistema. Isso irá prevenir que as transações gerem possíveis erros ou quebras ou ainda que caracteres especiais possam ser apresentados de maneira diferente do habitual.
 - Para que ocorra normalmente a geração de logs, certifique-se que o diretório e o arquivo de log tenham permissões de leitura e escrita.


[Dúvidas?]
----------

Em caso de dúvidas mande um e-mail para desenvolvedores@pagseguro.com.br


Contribuições
-------------

Achou e corrigiu um bug ou tem alguma feature em mente e deseja contribuir?

* Faça um fork.
* Adicione sua feature ou correção de bug.
* Envie um pull request no [GitHub].

  [1]: https://raw.githubusercontent.com/pagseguro/android/mvn-repo/br/com/uol/ps/library/0.1/library-0.1.jar
  [Android]: http://www.android.com/
  [GSon]: https://code.google.com/p/google-gson/
  [fórum]: http://forum.pagseguro.uol.com.br/
  [GitHub]: https://github.com/pagseguro/php/
  
  
 
