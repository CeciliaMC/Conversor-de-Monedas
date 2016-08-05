# Conversor-de-Monedas
package examenmo.com.facci.conversorCM;

import android.content.Context;
import android.content.SharedPreferences;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.EditText;
import android.widget.Spinner;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivityJB extends AppCompatActivity {
final String[] datos = new String[]{"DOLAR", "EURO", "PESO MEXICANO"};

    private Spinner monedaActualSP;
    private Spinner monedaCambioSP;
    private EditText valorCambioET;
    private TextView resultadoCM;

    final  private double factorDolarEuro = 0.87;
    final private  double factorPesoDolar = 0.54;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main_activity_jb);

        ArrayAdapter<String> adapadador = new ArrayAdapter<String>(this,R.layout.support_simple_spinner_dropdown_item,datos);

        monedaActualSP = (Spinner) findViewById(R.id.monedaActualSP);

        monedaActualSP.setAdapter(adapadador);

        monedaCambioSP = (Spinner) findViewById(R.id.monedaCambioSP);

        SharedPreferences preferencias = getSharedPreferences("MiPreferencia", Context.MODE_PRIVATE);

        String tmpMonedaActual = preferencias.getString("monedaActual", "");
        String tmpMonedaCambio = preferencias.getString("monedaCambio","");

        if(tmpMonedaActual.equals("")){
            int indice = adapadador.getPosition(tmpMonedaActual);
            monedaActualSP.setSelection(indice);
        }

        if(tmpMonedaCambio.equals("")){
            int indice = adapadador.getPosition(tmpMonedaCambio);
            monedaCambioSP.setSelection(indice);
        }
    }
