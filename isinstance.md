- `isinstance`  is a built in fuction in python whether rest is a Link, when passed `(rest, Link)` as arugments
- `help(ininstance)`: Return whether an object is an instance of a ***==class==*** or of a ***==subclass==*** thereof.
	- It's a little bit different than getting the `type` of class and checking whether it's exactly equal to class `Link` 
	- this , [[isinstance]](rest, Link),  is also `True` if rest is an instance of a class that inherits form Link
	- this is a good idea, now the system is extensible
		- If you want to build a special kind of link list, by inheritinng from link, we can simply ue the sme construtor, this veriifivation will strill workout as we expect
 