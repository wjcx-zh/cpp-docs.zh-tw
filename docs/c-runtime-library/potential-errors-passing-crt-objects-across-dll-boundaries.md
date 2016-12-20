---
title: "跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "DLL 衝突 [C++]"
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您將 C 時執行階段 \(CRT\) 物件的控制代碼 \(File Handle\)、地區設定和環境變數中或在 DLL \(跨 DLL 界限的函式呼叫之外\)，可能會發生未預期的行為，如果 DLL，以及呼叫 DLL 的檔案，使用 CRT 程式庫的不同複本。  
  
 有一個相關問題時，可能會發生您配置記憶體 \(明確與 `new` 或 `malloc`隱含地使用 `strdup`， `strstreambuf::str`，依此類推\) 然後透過 ABI 傳遞要釋放的 DLL 界限的指標。  如果 DLL 及其使用者使用 CRT 程式庫的不同複本，這可能會導致記憶體存取違規例或堆積損毀。  
  
 在偵錯期間，例如問題的另一個徵兆就是可以在輸出視窗中的錯誤:  
  
 堆積 \[\]:無效的位址指派給 RtlValidateHeap \# \(\#\)，  
  
## 原因  
 CRT 程式庫的每個複本都有個別的和不同狀態。  因此， CRT 物件 \(例如檔案控制代碼，環境變數，然後，地區設定為配置或設定這些物件 CRT 的複本才有效。  當 DLL 及其使用者使用 CRT 程式庫的不同複本時，可以在另一端無法透過跨 DLL 界限的這些 CRT 物件和預期它們正確挑選。  
  
 此外，因為 CRT 程式庫的每個複本都有自己的堆積管理員，配置記憶體中的 CRT 程式庫中並透過 ABI CRT 程式庫的不同複本會釋放的 DLL 界限的指標是堆積損毀的一個可能的原因。  
  
 如果您設計您的 DLL，以便透過 ABI 傳遞這個界限的 CRT 物件或配置記憶體和預期在 DLL 之外被釋放，您限制 DLL 使用者使用 CRT 程式庫的相同複本與 DLL。  只有兩個與 CRT DLL 的相同版本，連結 DLL 及其使用者使用 CRT 程式庫的相同複本。  這可能會造成問題，如果您使用 Visual C\+\+ 5.0 混合依 Visual C\+\+ 4.1 或之前建立的應用程式建置和 DLL。  由於 Visual C\+\+ 使用的 CRT 程式庫的 DLL 版本 4.1 是 msvcrt40.dll，而且視覺效果所使用的 SQL Server 5.0 是 msvcrt.dll，您不能建立自己的應用程式使用 CRT 程式庫的相同複本與這些 DLL。  
  
 但也有例外。  在美國英文版和 Windows 2000 其他當地語系化版本，例如德文、法文和捷克文，這個 msvcrt40.dll \(4.20 版\) 的轉送版本傳輸。  因此，即使 DLL 與 msvcrt40.dll 連接，而且其使用者與 msvcrt.dll 連接，您仍可使用 CRT 程式庫的相同複本，因為所有呼叫 msvcrt40.dll 轉送至 msvcrt.dll。  
  
 不過 msvcrt40.dll 這轉送版本是在 Windows 2000 一些當地語系化版本中無法使用，例如日文、韓文和中文。  因此，如果您的應用程式以這些作業系統，您需要為取得與 msvcrt40.dll DLL 的已升級的版本或修改應用程式不會依賴使用 CRT 程式庫的相同複本。  如果您開發的 DLL，這表示重建與 Visual C\+\+ 4.2 \(含\) 以後版本。  如果是協力廠商 DLL，您需要將升級的廠商。  
  
 請注意:這個轉送 DLL 版本 msvcrt40.dll \(4.20 版\) 無法轉散發。  
  
## 範例  
  
### 說明  
 這個範例會跨 DLL 界限之檔案控制代碼。  
  
 DLL 和 .exe 檔案是以 \/MD 建置，如此它們共用 CRT 的單一複本。  
  
 如果您重建與 \/MT，讓它們使用 CRT 的單獨的複本，執行這個產生的 test1Main.exe 造成存取違規。  
  
### 程式碼  
  
```  
// test1Dll.cpp  
// compile with: /MD /LD  
#include <stdio.h>  
__declspec(dllexport) void writeFile(FILE *stream)  
{  
   char   s[] = "this is a string\n";  
   fprintf( stream, "%s", s );  
   fclose( stream );  
}  
```  
  
### 程式碼  
  
```  
// test1Main.cpp  
// compile with: /MD test1dll.lib  
#include <stdio.h>  
#include <process.h>  
void writeFile(FILE *stream);  
  
int main(void)  
{  
   FILE  * stream;  
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );  
   writeFile(stream);  
   system( "type fprintf.out" );  
}  
```  
  
### Output  
  
```  
this is a string  
```  
  
## 範例  
  
### 說明  
 這個範例會跨 DLL 界限的環境變數。  
  
### 程式碼  
  
```  
// test2Dll.cpp  
// compile with: /MT /LD  
#include <stdio.h>  
#include <stdlib.h>  
  
__declspec(dllexport) void readEnv()  
{  
   char *libvar;  
   size_t libvarsize;  
  
   /* Get the value of the MYLIB environment variable. */   
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );  
  
   if( libvar != NULL )  
      printf( "New MYLIB variable is: %s\n", libvar);  
   else  
      printf( "MYLIB has not been set.\n");  
   free( libvar );  
}  
```  
  
### 程式碼  
  
```  
// test2Main.cpp  
// compile with: /MT /link test2dll.lib  
#include <stdlib.h>  
#include <stdio.h>  
  
void readEnv();  
  
int main( void )  
{  
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );  
   readEnv();  
}  
```  
  
### Output  
  
```  
MYLIB has not been set.  
```  
  
 如果 DLL 和 .exe 檔案是以 \/MD 建置，以便只使用 CRT 的複本，程式才能執行成功而且會產生下列輸出:  
  
```  
New MYLIB variable is: c:\mylib;c:\yourlib  
```  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)