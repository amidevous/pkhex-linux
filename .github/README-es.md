PKHeX
=====
![License](https://img.shields.io/badge/License-GPLv3-blue.svg)

Editor de guardado de las series principales de Pokémon, programado en [C#](https://es.wikipedia.org/wiki/C_Sharp).

Soporta los siguientes archivos:
* Archivos de guardado ("main", \*.sav, \*.dsv, \*.dat, \*.gci, \*.bin)
* Archivos de Memory Card de GameCube (\*.raw, \*.bin) que contienen archivos de GC Pokémon.
* Archivos de entidades individuales de Pokémon (.pk\*, \*.ck3, \*.xk3, \*.pb7, \*.sk2, \*.bk4, \*.rk4)
* Archivos de Regalos Misteriosos (\*.pgt, \*.pcd, \*.pgf, .wc\*) incluyendo conversión a .pk\*
* Importar archivos de entidades de GO Park (\*.gp1) incluyendo conversión a .pb7
* Importar equipos desde archivos Decrypted 3DS Battle Videos
* Pasar de una generación a la siguiente, convirtiendo los archivos en el proceso.

Los datos son visualizados en una forma que permite modificarlos y guardarlos.
La interfaz gráfica puede ser traducida con archivos de texto externos para dar soporte a múltiples lenguajes.

Pokémon Showdown asigna un código QR que puede ser importado/exportado para ayudar al compartir.

PKHeX espera archivos de guardado que no estén cifrados con las claves específicas de la consola. Use un gestor de archivos de guardado para importar y exportar información de la consola ([Checkpoint](https://github.com/FlagBrew/Checkpoint) o [JKSM](https://github.com/J-D-K/JKSM)).

**No apoyamos ni toleramos las trampas a expensas de otros. No uses un Pokémon modificado significativamente en batalla o en intercambios con quienes no estén al tanto de que estás usando un Pokémon modificado.**

## Capturas de Pantalla

![Pantalla principal](https://i.imgur.com/oM407mV.png)

## Instalar

Última versión binaria de Windows

https://projectpokemon.org/home/files/file/1-pkhex/

Paquetes de Linux versión 22.12.18 último trabajo en Wine

https://software.opensuse.org//download.html?project=home%3Aamidevousgmail%3Apkhex&package=pkhex

## Compilación

PKHeX es una aplicación de Windows Forms que requiere [.NET 8.0](https://dotnet.microsoft.com/download/dotnet/8.0).

El archivo ejecutable puede ser construido con cualquier compilador que soporte C# 12.

### Configuraciones del Build

Para hacer el build puedes usar las configuraciones de Debug o de Release. ¡No hay que preocuparse por código específico de ninguna plataforma!

## Dependencias

La generación de códigos QR de PKHeX es la de [QRCoder](https://github.com/codebude/QRCoder), licenciado bajo [la licencia MIT](https://github.com/codebude/QRCoder/blob/master/LICENSE.txt).

La colección de sprites de Pokémons Shiny de PKHeX fue tomada de [pokesprite](https://github.com/msikma/pokesprite), licenciado bajo [la licencia MIT](https://github.com/msikma/pokesprite/blob/master/LICENSE).

PKHeX's Pokémon Legends: Arceus sprite collection is taken from the [National Pokédex - Icon Dex](https://www.deviantart.com/pikafan2000/art/National-Pokedex-Version-Delta-Icon-Dex-824897934) project and its abundance of collaborators and contributors.

### IDE

PKHeX se puede abrir con un IDE como [Visual Studio](https://visualstudio.microsoft.com/es/downloads/), abriendo los archivos .sln o .csproj.

## Compilación para Linux o MacOSX versión en línea 22.12.18, último trabajo en Wine

instale Wine 9.0 (requiere multiarca) o + y Winetricks 20240105 o +

```
git clone https://github.com/kwsch/PKHeX.git
DESTDIR=$PWD/build make DESTDIR=$PWD/build install
sudo mv $PWD/build/* /
```



manual completo

```
wget https://github.com/amidevous/PKHeX/releases/download/24.01.12/PKHeX.221218.zip -O PKHeX.221218.zip
rm -f "PKHeX.exe"
unzip PKHeX.221218.zip
rm -f PKHeX.221218.zip
install -D -m 644 "PKHeX.exe" "$HOME/.local/share/pkhex/PKHeX.exe"
install -d "$HOME/.local/share/pkhex/"
install -d "$HOME/.local/share/pkhex/wineprefixes/pkhex"
install -d "$HOME/.local/share/pkhex/wineprefixes/pkhex/drive_c"
wget "https://raw.githubusercontent.com/amidevous/PKHeX/master/launcher" -O "launcher"
sudo install -D -m 755 "launcher" "/usr/bin/pkhex"
wget "https://raw.githubusercontent.com/amidevous/PKHeX/master/icon.png" -O "icon.png"
sudo install -D -m 644 "icon.png" "/usr/share/pixmaps/pkhex.png"
wget "https://raw.githubusercontent.com/amidevous/PKHeX/master/pkhex.desktop" -O "pkhex.desktop"
sudo install -D -m 644 "pkhex.desktop" "/usr/usr/share/applications/pkhex.desktop"
WINEPREFIX="$HOME/.local/share/pkhex/wineprefixes/pkhex" winetricks -q --force dotnet40 dotnet45 dotnet452 dotnet46 dotnet461 dotnet462 dotnet471 dotnet472 dotnet48 dotnetcoredesktop3 dotnetdesktop6 win10 >/dev/null 2>&1
```
