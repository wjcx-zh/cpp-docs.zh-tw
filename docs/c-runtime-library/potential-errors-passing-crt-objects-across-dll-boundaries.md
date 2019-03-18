---
title: 跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤
ms.date: 11/04/2016
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 31f9d9aceba167b516c9d37724e240f1bc4586e1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749892"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤

當您將 C 執行階段 (CRT) 物件 (例如檔案控制代碼、地區設定和環境變數) 傳遞進出 DLL (跨 DLL 界限的函式呼叫) 時，如果 DLL 以及呼叫 DLL 的檔案使用不同複本的 CRT 程式庫，可能會發生未預期的行為。

當您配置記憶體 (明確使用 `new` 或 `malloc`，或隱含使用 `strdup`、`strstreambuf::str`，依此類推)，然後跨 DLL 界限傳遞要被釋放的指標時，可能會發生相關的問題。 如果 DLL 和它的使用者使用不同複本的 CRT 程式庫，這可能會造成記憶體存取違規或堆積損毀。

此問題的另一個症狀可能是偵錯期間在輸出視窗中的錯誤，例如︰

HEAP[]：指定至 RtlValidateHeap(#,#) 的位址無效

## <a name="causes"></a>原因

應用程式或 DLL 在執行緒區域儲存區中保留的每一份 CRT 程式庫複本都有個別且不同的狀態。 因此，CRT 物件 (例如檔案控制代碼、環境變數和地區設定) 只對於應用程式或 DLL 中配置或設定這些物件的 CRT 複本有效。 當 DLL 及其應用程式用戶端使用不同複本的 CRT 程式庫時，您無法跨 DLL 界限傳遞這些 CRT 物件，並預期能在另一端正確挑選出這些物件。 這在 Visual Studio 2015 及更新版本中的通用 CRT 之前的 CRT 版本更是如此。 使用 Visual C++ 2013 或更早版本建置的每個 Visual Studio 版本，都有一個版本特定的 CRT 程式庫。 CRT 的內部實作詳細資料 (例如其資料結構和命名慣例) 在每個版本中都不同。 我們從未支援將針對某個版本的 CRT 編譯的程式碼動態連結到不同版本的 CRT DLL，雖然這偶爾可以運作，但這是幸運而非刻意設計如此。

此外，因為每一份 CRT 程式庫複本有自己的堆積管理員，在一個 CRT 程式庫中配置記憶體，並且跨 DLL 界限傳遞要由不同 CRT 程式庫複本釋放的指標，可能是堆積損毀的潛在原因。 如果您設計 DLL 讓它跨界限傳遞 CRT 物件或配置記憶體並預期它會在 DLL 外釋放時，您要限制 DLL 的應用程式用戶端使用與 DLL 相同的 CRT 程式庫複本。 DLL 及其用戶端通常只有在兩者在載入時都連結至相同版本的 CRT DLL 時，才會使用相同複本的 CRT 程式庫。 因為在 Windows 10 上 Visual Studio 2015 及更新版本所使用通用 CRT 程式庫的 DLL 版本現在是一個集中部署的 Windows 元件 ucrtbase.dll，所以它也適用於使用 Visual Studio 2015 及更新版本建置的應用程式。 不過，即使 CRT 程式碼完全相同，您也無法將在一個堆積中配置的記憶體遞交給使用不同堆積的元件。

## <a name="example"></a>範例

### <a name="description"></a>說明

這個範例會跨 DLL 界限傳遞檔案控制代碼。

DLL 和 .exe 檔案是使用 /MD 建置，所以它們共用一個複本的 CRT。

如果您使用 /MT 重建而讓它們使用不同的 CRT 複本，執行產生的 test1Main.exe 會造成存取違規。

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
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

```Output
this is a string
```

## <a name="example"></a>範例

### <a name="description"></a>說明

這個範例會跨 DLL 界限傳遞環境變數。

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
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

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

如果 DLL 和 .exe 檔案兩者都使用 /MD 建置，因此只使用一個 CRT 複本，程式會順利執行並產生下列輸出︰

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
