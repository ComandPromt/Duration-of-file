# Duration-of-file

## Maven

~~~

<dependency>
  <groupId>com.drewnoakes</groupId>
  <artifactId>metadata-extractor</artifactId>
  <version>2.14.0</version>
</dependency>

~~~

~~~java

			private String saberDuracion(String archivo) throws ImageProcessingException, IOException {
				
				InputStream inputstream = new FileInputStream(archivo);

				Metadata metadata = ImageMetadataReader.readMetadata(inputstream);

				String etiqueta = "";
				
				String duracion = "";
				
				for (Directory directory : metadata.getDirectories()) {

					for (Tag tag : directory.getTags()) {

						etiqueta = tag.toString();

						if (etiqueta.contains("Duration in Seconds")) {
							duracion = etiqueta.substring(etiqueta.indexOf("- ") + 2, etiqueta.length());
						}

					}

				}

				return duracion;
        
			}
            
~~~
