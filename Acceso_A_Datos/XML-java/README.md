
# XML java
## Posibles errores
- No tener las librerias correctas

  [aqui](https://github.com/javiLeL/XML-java/blob/main/Librerias.txt) estan las librerias que se deben importar
## Leer
- Obtención de un DocumentBuilder
    ```java
    DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
    DocumentBuilder builder = factory.newDocumentBuilder();
    Document document = builder.parse(new File(nombre_archivo));
    ```
    Donde `nombre_archivo` es una String con el nombre donde esta el archivo

- Recorrer el Documento
    
    Creamos una lista de nodos con:
    ```java
    NodeList nodeList = document.getElementsByTagName(nombre_nodo);
    ```
    Donde el `nombre_nodo` es el nombre de la etiqueta que queremos buscar
    
    Pasamos al apartado de recoger datos:
    ```java
    for (int i = 0; i < nodeList.getLength(); i++) {
        Node node = nodeList.item(i);
        if (node.getNodeType() == Node.ELEMENT_NODE) {
            Element element = (Element) node;

            // Para obtener un Elemento: 
            String nombre_elemento = element.getElementsByTagName(nombre_del_elemento).item(0).getTextContent();

            // Para obtener un Atributo
            String nombre_id = element.getAttribute(nombre_del_atributo)
        }
    }
    ```
    Donde `nombre_del_elemento` es el nombre de la etiqueta de la que se desea obtener la informacion
    
    Donde `nombre_del_atributo` es el nombre del atributo que se desea obtener

    *Solo puede ser de tipo `String`*

## Escribir
 - Creacion de un DocumentBuilder 
    ```java
    DocumentBuilderFactory documentFactory = DocumentBuilderFactory.newInstance();
    DocumentBuilder documentBuilder = documentFactory.newDocumentBuilder();
    Document document = documentBuilder.newDocument();
    ```

- Creacion del element raiz
    ```java
    Element root = document.createElement(nombre_elemento_root);
    document.appendChild(root);
    ```
    Donde `nombre_elemento_root` es el nombre de la etiqueta `root`

- Creacion de los elementos hijos del elemento raiz

    *Para esta parte es recomendable hacer un `DTO`, hacer una lista de este tipo de clase y con esta lista sera con lo que operaremos*
    ```java
    for (DTO dato : listaDatos){
        // Creamos el elemento del objeto dentro del elemento root:
        Element datoElement = document.createElement(dato_elemento_nombre);

        // Opcional se le puede pasar un atributo
        datoElement.setAttribute(nombre_del_atributo, valor_del_atributo);

        root.appendChild(datoElement);

        // Creamos mas elementos dentro del elemento del objeto creado:
        Element valorElement = document.createElement(valor_elemento);
        valorElement.appendChild(document.createTextNode(dato.get_nombre_valor()));
        datoElement.appendChild(valorElement);

    }
    ```
    Donde `dato_elemento_nombre` sera el nombre del elemento o elementos que contendra el elemeto `root`
    
    Donde `valor_del_atributo` sera el valor que obtendra el atributo del elemento `datoElement`

    Donde `valor_elemento` sera el valor que obtendra el elemento `valorElement`

    *Solo puede ser de tipo `String`*

- *Ejemplo para crear los atributos de tipo id*
  ```java
  int id=1;
  for (DTO dato : listaDatos){
    ...
    datoElement.setAttribute("id", String.valueOf(id++));
    ...
  }
  ```
  
  Esto hara que se incremente la id de forma automatica al escribirse
  
- Escribir el contenido a un archivo XML
    ```java
    TransformerFactory transformerFactory = TransformerFactory.newInstance();
    Transformer transformer = transformerFactory.newTransformer();
    transformer.setOutputProperty(OutputKeys.INDENT, "yes");        
    DOMSource domSource = new DOMSource(document);
    StreamResult streamResult = new StreamResult(new File(nombre_archivo));
    transformer.transform(domSource, streamResult);
    ```
    Donde `nombre_archivo` es el nombre del archivo que se escribira o se sobre escribira
  
## Creadores
[@javiLeL](https://github.com/javiLeL)
