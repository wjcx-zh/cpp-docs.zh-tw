---
title: 跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤
description: 概述您在跨動態連結程式庫傳遞 Microsoft C 執行時間物件時可能遇到的潛在問題， (DLL) 界限。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: f6d831ac8b86be8a6669e8ee6c66da64507d129f
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590182"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>跨 DLL 界限傳遞 CRT 物件時可能發生的錯誤

當您將 C 執行時間 (CRT) 物件（例如檔案控制代碼、地區設定和環境變數）移入或移出 DLL 時，透過 DLL 界限的函式呼叫，如果 DLL 或任何呼叫 DLL 的檔案使用不同的 CRT 程式庫複本，就會發生未預期的行為。

當您配置記憶體 (明確地使用 `new` 或 `malloc` 、或以隱含方式使用 `strdup` 、等) ，然後將 `strstreambuf::str` 指標傳遞到釋放的 DLL 界限上時，就會發生相關的問題。 如果 DLL 和其取用者使用不同的 CRT 程式庫複本，這可能會導致記憶體存取違規或堆積損毀。

此問題的另一個徵兆是在偵錯工具期間輸出視窗中的錯誤，例如 `HEAP[]: Invalid Address specified to RtlValidateHeap(#,#)`

## <a name="causes"></a>原因

應用程式或 DLL 在執行緒區域儲存區中保留的每一份 CRT 程式庫複本都有個別且不同的狀態。

CRT 物件（例如檔案控制代碼、環境變數和地區設定）僅適用于配置或設定這些物件之應用程式或 DLL 中的 CRT 複本。 當 DLL 和其用戶端使用不同的 CRT 程式庫複本時，您無法跨 DLL 界限傳遞這些 CRT 物件，並預期會在另一端正確使用它們。 這適用于在 Visual Studio 2015 和更新版本中的通用 CRT 之前的 CRT 版本。

使用 Visual Studio 2013 或更早版本建置的每個 Visual Studio 版本都有一個版本特定 CRT 程式庫。 CRT 的內部執行詳細資料（例如資料結構和命名慣例）在每個版本中都不同。 從未支援將針對某個 CRT 版本編譯的程式碼動態連結至不同版本的 CRT DLL。 有時它可以運作，但因為很幸運而非設計。

由於 CRT 程式庫的每個複本都有自己的堆積管理員，因此在一個 CRT 程式庫中配置記憶體，並將指標傳遞至 DLL 界限，以由不同的 CRT 程式庫複本釋出，可能會造成堆積損毀。 如果您設計 DLL 以便跨 DLL 界限傳遞 CRT 物件，或是配置記憶體，並預期它會在 DLL 外部釋放，則 DLL 的用戶端必須使用與 DLL 相同的 CRT 程式庫複本。

DLL 及其用戶端通常只有在兩者在載入時都連結至相同版本的 CRT DLL 時，才會使用相同複本的 CRT 程式庫。 由於 Visual Studio 2015 和更新版本所使用的通用 CRT 程式庫 DLL 版本（Windows 10）現在是集中部署的 Windows 元件 ( # A0) ，因此以 Visual Studio 2015 和更新版本所建立的應用程式也是相同的。 但是，即使 CRT 程式碼完全相同，您也無法將在某個堆積中配置的記憶體，提供給使用不同堆積的元件。

## <a name="example"></a>範例

### <a name="description"></a>描述

這個範例會跨 DLL 界限傳遞檔案控制代碼。

DLL 和 .exe 檔案是使用建立的 `/MD` ，因此它們會共用 CRT 的單一複本。

如果您使用重建 `/MT` ，使其使用不同的 CRT 複本，執行產生的 **test1Main.exe** 會導致存取違規。

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

### <a name="description"></a>描述

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

如果 DLL 和 .exe 檔案都已建立， `/MD` 只使用一個 CRT 複本，則程式會成功執行並產生下列輸出：

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
