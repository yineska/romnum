# romnum
package rom;

import java.util.HashMap;
import java.util.Map;

import javax.swing.JOptionPane;

public class conv {
	public static int centenas = 0, decenas = 0, unidades = 0;
	public static String [][] romanos={{"","I","II","III","IV","V","VI","VII","VIII","IX"},
	         							{"","X","XX","XXX","XL","L","LX","LXX","LXX","XC"},
	         							{"","C"}};
	public static void main(String[] args) {
			int num,select,pro;
			boolean salir=false;
			String romano,sn;
			select=Integer.parseInt(JOptionPane.showInputDialog("Seleccione una Opcion : \n \n  1.Conversor de ROMANO a ARABIGO.\n 2.Conversor de ARABIGO a ROMANO. \n 3.salir"));
			switch(select) {
			case 1:
				sn=(JOptionPane.showInputDialog("Ingrese un numero Romano entre 1 y 100: "));
				pro=arabigo(sn);
				JOptionPane.showMessageDialog(null, "El numero en Arabigo es:"+pro, "RESULTADOS " , JOptionPane.INFORMATION_MESSAGE);
				break;


			case 2:
				num=Integer.parseInt(JOptionPane.showInputDialog("Ingrese un numero Arabigo entre 1 y 100: "));
				obtenerNotDesarrollada(num);
				romano=obtenerRomano();
				JOptionPane.showMessageDialog(null, "El numero en Romano es:"+romano, "RESULTADOS " , JOptionPane.INFORMATION_MESSAGE);
				break;
			case 3:
				salir=true;
				break;

				default:
				break;
}
}



	public static void obtenerNotDesarrollada(int numero) {
	      centenas = (int)numero % 1000 / 100;
	      decenas = (int)numero % 1000 % 100 / 10;
	      unidades = (int)numero % 1000 % 100 % 10;
	   }

	public static String obtenerRomano(){
	      return 
	            romanos[2][centenas]+""+
	            romanos[1][decenas]+""+
	            romanos[0][unidades]+"";
	   }

	public static int arabigo(String roman_numeral) {
        Map<Character, Integer> roman_char_dict = new HashMap<Character, Integer>();
        roman_char_dict.put('I', 1);
        roman_char_dict.put('V', 5);
        roman_char_dict.put('X', 10);
        roman_char_dict.put('L', 50);
        roman_char_dict.put('C', 100);
        int pro1 = 0;
        for (int i = 0; i < roman_numeral.length(); i += 1) {
            if (i == 0 || roman_char_dict.get(roman_numeral.charAt(i)) <= roman_char_dict.get(roman_numeral.charAt(i - 1)))
                pro1 += roman_char_dict.get(roman_numeral.charAt(i));
            else
                pro1 += roman_char_dict.get(roman_numeral.charAt(i)) - 2 * roman_char_dict.get(roman_numeral.charAt(i - 1));
        }
        return pro1;
    }


}
