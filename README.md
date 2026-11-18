# Venta cruzada en telecomunicaciones con reglas de asociación

Análisis de cesta de mercado (*market basket analysis*) sobre 1.763 clientes de una operadora de telecomunicaciones para descubrir qué servicios se contratan juntos y convertirlo en packs y recomendaciones comerciales.

![Top combinaciones de servicios](images/top_combinaciones.png)
![Heatmap](images/heatmap_lift.png)

## Problema de negocio

La operadora quiere aumentar el ingreso por cliente sin elevar el coste de captación. La pregunta es: **¿qué servicio conviene ofrecer a cada cliente según lo que ya tiene contratado?**

## Datos

- Dataset público basado en *IBM Telco Customer Churn* (1.763 clientes, 21 variables).
- Cada cliente se trata como una "cesta" de 9 servicios: telefonía, líneas múltiples, internet, seguridad online, backup, protección de dispositivo, soporte técnico, streaming TV y streaming de películas.

## Metodología

1. **Preparación:** conversión de cada servicio a binario (1 = contratado, 0 = no contratado).
2. **Apriori:** itemsets frecuentes con soporte mínimo del 15 %.
3. **Reglas de asociación:** reglas con confianza ≥ 50 %, ordenadas por *lift*.
4. **Depuración:** se excluyen telefonía e internet de las reglas porque son servicios base que generan reglas redundantes.

## Resultados principales

| Hallazgo | Dato |
| --- | --- |
| Servicio más contratado | Telefonía (89 % de los clientes) |
| Regla más fuerte | Protección de dispositivo + Streaming TV → Streaming de películas (confianza 78 %, lift 2,06) |
| Mejor acompañante de las líneas múltiples | Streaming TV (lift 1,40) |
| Segmento con pareja | 48 % ya combina telefonía + líneas múltiples |

## Recomendaciones de negocio

1. **Pack de entretenimiento:** Streaming TV + Streaming de películas, con precio inferior a la suma por separado.
2. **Promoción móvil + streaming:** ofrecer streaming a clientes con líneas múltiples, que tienen 1,4 veces más propensión a contratarlo.
3. **Campaña para clientes con pareja (San Valentín):** dirigida a todo el segmento, sin separar por género (50,7 % hombres vs. 45,7 % mujeres).
4. **Recomendador "next best offer":** sugerir automáticamente el consecuente con mayor confianza cuando el cliente contrata el antecedente.

## Estructura del repositorio

    data/raw/          Dataset original
    notebooks/         Análisis paso a paso
    images/            Gráficas del README
    requirements.txt   Librerías necesarias

## Cómo reproducirlo

    git clone https://github.com/oyaxcal/telco-cross-selling-association-rules.git
    cd telco-cross-selling-association-rules
    pip install -r requirements.txt
    jupyter notebook notebooks/01_association_rules.ipynb

## Tecnologías

Python · Pandas · NumPy · Matplotlib · Seaborn · mlxtend

## Autor

**Olivia Yaxcal** · [LinkedIn]([https://www.linkedin.com/in/olivia-yaxcal/])
