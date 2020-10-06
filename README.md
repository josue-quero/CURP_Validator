# Validation of CURP and Name (CURP_Validator)

CURP_Validator it's a simple Python class that compares a given curp to a full name to determine if they coincide. With the given CURP, the class gets the information 
necessary to obtain the name of the person: "Nombres de pila", "Apellido Paterno", "Apellido Materno" .

**Atention**: The class does not take into account if other parts of the CURP like state, or birthday are valid. Nevertheless this shouln't be hard to implement.

---python
>>> from CURPValidator import CURPValidator
>>> CURPValidator.validate('POPC990709MGTSRL02', 'CLAUDIA LEONOR POSADA PEREZ')
{'nombre': 'CLAUDIA LEONOR', 'apellido': 'POSADA', 'apellido_m': 'PEREZ'}
	
# It works with prefixes such as: Del, De la, De los, etc
>>> CURPValidator.validate('MAGE981117MMNCRS05', 'ESTEFANIA DE LOS DOLORES MACIAS GARCIA')
{'nombre': 'ESTEFANIA DE LOS DOLORES', 'apellido': 'MACIAS', 'apellido_m': 'GARCIA'}

>>> CURPValidator.validate('MAQD990926HOCRRV00', 'DAVID JOSUE MARCIAL QUERO')
{'nombre': 'SANDRA DEL CARMEN', 'apellido': 'MARTINEZ', 'apellido_m': 'DE LA PAZ'}
	
# It detects the lack of a second surname
>>> CURPValidator.validate('TAXA990915MNEMXM06', 'AMBER NICOLE TAMAYO')
{'nombre': 'AMBER NICOLE', 'apellido': 'TAMAYO', 'apellido_m': ''}
	
# It detects words that are "altisonantes"
>>> CURPValidator.validate('MXME991209MGRRSS07', 'ESMERALDA MARTINEZ MASTACHE ')
{'nombre': 'ESMERALDA', 'apellido': 'MARTINEZ', 'apellido_m': 'MASTACHE'}

# Returns False in the case of not including a name or CURP
>>> CURPValidator.validate('MACD990727MMMCRRN0', 'DANIELA IVETTE MARTINEZ CRUZ')
False
---
	 
This program is distributed under the GNU 2.0 licence, for more information please vistit the site: [Free Software Foundation](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) 

