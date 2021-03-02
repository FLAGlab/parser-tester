# Parser-tester
This repository contains the base project to test language parsers built with JavaCC


# Usage
To use the parser-tester you should create a new Java project in Eclipse, and copy the contents of the repository into the project

- Language definitions are/go in the `languages` package
- To use the tester, you must add a reference to the parser in the `MundoParsers` as:

``` 
public MyParser getMyParser(){
  return new MyParser(System.in);
} 
```  

You are also required to modify the hook method `procesarCadena(String texto)` in the same class
```
if(parsers.get(currentParser).equals("My Parser")){
	Expressions parserExpressions = getParserExpressions();
	parserExpressions.ReInit(new java.io.StringReader(texto));
	try {
			parserExpressions.one_line(); 
		  resp = new String("OK \n");
	} catch (Exception e) {
		  resp = new String ("Error de Sintaxis: "+e.getMessage());
  } catch (Error e) {
		  resp = new String ("Error Lexico: "+e.getMessage());
	}
}
```
