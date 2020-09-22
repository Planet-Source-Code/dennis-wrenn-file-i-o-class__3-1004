<div align="center">

## File I/O class\.


</div>

### Description

a class to make using fstream easier.

NOTE: after a call to openfile() it is HIGHLY recomended to call closefile()
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Dennis Wrenn](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/dennis-wrenn.md)
**Level**          |Intermediate
**User Rating**    |4.0 (8 globes from 2 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+
**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__3-2.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/dennis-wrenn-file-i-o-class__3-1004/archive/master.zip)





### Source Code

```
#include <fstream>
#include <cstdio>
#include <string>
using namespace std;
const READ = 0;
const WRITE = 1;
/*
ios::app -- Opens the file, and allows additions at the end
ios::ate -- Opens the file, but allows additions anywhere
ios::trunc -- Deletes everything in the file
ios::nocreate -- Does not open if the file must be created
ios::noreplace -- Does not open if the file already exists
*/
const ate = 4;
const app = 8;
const trunc = 16;
const nocreate = 32;
const nereplace = 64;
class file
{
public:
file();
~file();
void openfile(string filename, int readwrite, int mode);
void closefile(int readwrite);
void writefile(string text);
void renamefile(string from, string to);
void deletefile(string filename);
string getcontents();
protected:
ifstream ifile;
ofstream ofile;
};
file::file()
{
}
file::~file()
{
}
void file::openfile(string filename, int readwrite, int mode = nocreate)
{
	switch (readwrite)
	{
		case READ:
			ifile.open(filename.c_str(), mode);
			break;
		case WRITE:
			ofile.open(filename.c_str(), mode);
			break;
	}
}
void file::closefile(int readwrite)
{
	switch (readwrite)
	{
		case READ:
			ifile.close();
			break;
		case WRITE:
			ofile.close();
			break;
	}
}
string file::getcontents()
{
	string str = "";
	char f;
	while(ifile.get(f))
		str += f;
	return str;
}
void file::writefile(string text)
{
	ofile << text;
}
void file::renamefile(string from, string to)
{
	rename(from.c_str(), to.c_str());
}
void file::deletefile(string filename)
{
	remove(filename.c_str());
}
```

