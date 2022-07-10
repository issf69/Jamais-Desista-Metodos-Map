# Jamais-Desista-Metodos-Map
Collections Java métodos Map - parte 1
## package jamaisdesista.com.br;

import java.util.*;

public class Exemplo1Map {
    public static void main(String[] args) {
/*
 Dada os modelos dos carros e seus respectivos consumos na estrada, faça:
 modelo = ferrari - consumo = 14,4km/l
 modelo = volkswagen - consumo = 15,6 km/l
 modelo = brasilia - consumo = 16,1 km/l
 modelo = corcel - consumo = 14,5 km/l
 modelo = kombi - consumo = 15,6 km/l
 */

//        Map carrosPopulares2020 = new HashMap(); //antes do java 5
//        Map<String, Double> carrosPopulares = new HashMap<>(); //Generics(jdk 5) - Diamont Operator(jdk 7)
//        HashMap<String, Double> carrosPopulares = new HashMap<>();
//        Map<String, Double> carrosPopulares2020 = Map.of("ferrari ", 14.4, "volkswagen", 15.6, "brasilia", 16.1, "corcel", 14.5, "kombi", 15.6)

        System.out.println("Crie um dicionario que relacione os modelos e seus respectivos consumos: ");
        Map<String, Double> carrosPopulares = new HashMap<>() {{
            put("ferrari", 14.4);
            put("volkswagen", 15.6);
            put("brasilia", 16.1);
            put("corcel", 14.5);
            put("kombi", 15.6);
        }};
        System.out.println(carrosPopulares.toString());

        System.out.println("Substitua o consumo do ferrari por 15,2 km/l: ");
        carrosPopulares.put("ferrari", 15.2);
        System.out.println(carrosPopulares);

        System.out.println("Confira se o modelo tucson esta no dicionario: " + carrosPopulares.containsKey("tucson"));

        System.out.println("Exiba o consumo do volkswagen: " + carrosPopulares.get("volkswagen"));

//        System.out.println("Exiba o terceiro modelo adicionado: ");

        System.out.println("Exiba os modelos: ");
        Set<String> modelos = carrosPopulares.keySet();
        System.out.println(modelos);

        System.out.println("Exiba os consumos dos carros: ");
        Collection<Double> consumos = carrosPopulares.values();
        System.out.println(consumos);

        System.out.println("Exiba o modelo mais economico e seu consumo: ");

        Double consumoMaisEficiente = Collections.max(carrosPopulares.values());
        Set<Map.Entry<String, Double>> entries = carrosPopulares.entrySet();
        String modeloMaisEficiente = "";

        for (Map.Entry<String, Double> entry : entries) {
            if (entry.getValue().equals(consumoMaisEficiente)) {
                modeloMaisEficiente = entry.getKey();
                System.out.println("Modelo mais eficiente: " + modeloMaisEficiente + " - " + consumoMaisEficiente);
            }
        }

        System.out.println("Exiba o modelo menos economico e seu consumo: " );

        Double consumoMenosEficiente = Collections.min(carrosPopulares.values());
        String modeloMenosEficiente = "";
        for (Map.Entry<String, Double> entry: carrosPopulares.entrySet()) {
            if(entry.getValue().equals(consumoMenosEficiente)) {
                modeloMenosEficiente = entry.getKey();
                System.out.println("Modelo menos eficiente: " + modeloMenosEficiente + " - " + consumoMenosEficiente);
            }
        }

        Iterator<Double> iterator = carrosPopulares.values().iterator();
        Double soma = 0d;
        while(iterator.hasNext()){
            soma += iterator.next();
        }
        System.out.println("Exiba a soma dos consumos: " + soma);

        System.out.println("Exiba a media dos consumos deste dicionario de carros: " + (soma/carrosPopulares.size()));

        System.out.println(carrosPopulares);
        System.out.println("Remova os modelos com o consumo igual a 15,6 km/l: ");
        Iterator<Double> iterator1 = carrosPopulares.values().iterator();
        while(iterator1.hasNext()){
            if(iterator1.next().equals(15.6)) iterator1.remove();
        }
        System.out.println(carrosPopulares);

        System.out.println("Exiba todos os carros na ordem em que foram informados: ");
        Map<String, Double> carrosPopulares1 = new LinkedHashMap<>() {{
            put("ferrari", 14.4);
            put("volkswagen", 15.6);
            put("brasilia", 16.1);
            put("corcel", 14.5);
            put("kombi", 15.6);
        }};
        System.out.println(carrosPopulares1.toString());

        System.out.println("Exiba o dicionario ordenado pelo modelo: ");
        Map<String, Double> carrosPopulares2 = new TreeMap<>(carrosPopulares1);
        System.out.println(carrosPopulares2.toString());

        System.out.println("Apague o dicionario de carros: ");
        carrosPopulares.clear();

        System.out.println("Confira se o dicionario esta vazio: " + carrosPopulares.isEmpty());
    }
}
### C:\Users\Irene\.jdks\openjdk-18.0.1.1\bin\java.exe "-javaagent:C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2022.1.1\lib\idea_rt.jar=61238:C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2022.1.1\bin" -Dfile.encoding=UTF-8 -classpath "C:\Users\Irene\Documents\Collections Java métodos Map - parte 1\MEtodos-Map-parte1\out\production\MEtodos-Map-parte1" jamaisdesista.com.br.Exemplo1Map
Crie um dicionario que relacione os modelos e seus respectivos consumos: 
{corcel=14.5, kombi=15.6, brasilia=16.1, ferrari=14.4, volkswagen=15.6}
Substitua o consumo do ferrari por 15,2 km/l: 
{corcel=14.5, kombi=15.6, brasilia=16.1, ferrari=15.2, volkswagen=15.6}
Confira se o modelo tucson esta no dicionario: false
Exiba o consumo do volkswagen: 15.6
Exiba os modelos: 
[corcel, kombi, brasilia, ferrari, volkswagen]
Exiba os consumos dos carros: 
[14.5, 15.6, 16.1, 15.2, 15.6]
Exiba o modelo mais economico e seu consumo: 
Modelo mais eficiente: brasilia - 16.1
Exiba o modelo menos economico e seu consumo: 
Modelo menos eficiente: corcel - 14.5
Exiba a soma dos consumos: 77.0
Exiba a media dos consumos deste dicionario de carros: 15.4
{corcel=14.5, kombi=15.6, brasilia=16.1, ferrari=15.2, volkswagen=15.6}
Remova os modelos com o consumo igual a 15,6 km/l: 
{corcel=14.5, brasilia=16.1, ferrari=15.2}
Exiba todos os carros na ordem em que foram informados: 
{ferrari=14.4, volkswagen=15.6, brasilia=16.1, corcel=14.5, kombi=15.6}
Exiba o dicionario ordenado pelo modelo: 
{brasilia=16.1, corcel=14.5, ferrari=14.4, kombi=15.6, volkswagen=15.6}
Apague o dicionario de carros: 
Confira se o dicionario esta vazio: true

Process finished with exit code 0
