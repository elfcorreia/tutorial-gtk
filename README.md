# Tutorial para compilar aplicações GTK no GNU/Linux

O [GTK](https://www.gtk.org/) é uma biblioteca de interface gráfica muito utilizada em sistemas GNU/Linux. Nesse tutorial mostraremos como preparar sua infraestrutura para compilar aplicações que fazem uso da biblioteca GTK.

Uma aplicação GTK simples que exibe uma janela em branco pode ser escrita da seguinte forma:
```cpp
#include <gtk/gtk.h>

int main(int argc, char *argv[]) {
	
	gtk_init(&argc, &argv);

	GtkWidget *janela;
	janela = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_show_all(janela);

	gtk_main();

	return 0;
}
```
Para compilar essa aplicação usaremos o compilador de C++ disponibilizado no GCC.



Para compilar devemos incluir as bibliotecas do GTK:

Este comando imprime as opções para a compilação de códigos com GTK

$ pkg-config --cflags gtk+-3.0

Este outro comando imprime as opções para ligação de executáveis com GTK

$ pkg-config --libs gtk+-3.0

Compile o seu programa dessa forma, usando os comandos anteriores:

$ g++ $(pkg-config --cflags gtk+-3.0) main.cpp -o main $(pkg-config --libs gtk+-3.0)
