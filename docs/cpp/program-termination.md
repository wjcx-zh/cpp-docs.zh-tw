---
title: C + + 程式終止
description: 描述 exit c + + 語言程式的方法。
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: fd0c7699ae032b5551f4fbc37eb3b7fa999a168f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352917"
---
# <a name="c-program-termination"></a>C + + 程式終止

在 c + + 中，您可以透過 exit 下列方式來執行程式：

- 呼叫 [exit](../c-runtime-library/reference/exit-exit-exit.md) 函數。
- 呼叫 [abort](../c-runtime-library/reference/abort.md) 函數。
- 從執行 [return](return-statement-cpp.md) 語句 `main` 。

## <a name="no-locexit-function"></a>exit 函式

在中宣告的函式會 [exit](../c-runtime-library/reference/exit-exit-exit.md) \<stdlib.h> 終止 c + + 程式。 提供做為引數的值 `exit` ，是 return 作業系統的程式 return 代碼或程式碼 exit 。 依照慣例， return 代碼為零表示程式已順利完成。 您可以使用 EXIT_FAILURE 的常數，也可以在中定義 EXIT_SUCCESS， \<stdlib.h> 表示程式的成功或失敗。

從函式發出 **`return`** 語句 `main` 相當於以 `exit` return 值做為其引數來呼叫函式。

## <a name="no-locabort-function"></a>abort 函式

函式 [abort](../c-runtime-library/reference/abort.md) 也會在標準 include 檔中宣告 \<stdlib.h> ，以終止 c + + 程式。 和之間的差異在於，可 `exit` `abort` `exit` 讓 c + + 執行時間終止處理發生 (全域物件的析構函數將會被呼叫) ，而 `abort` 立即終止程式。 函式會 `abort` 略過初始化的全域靜態物件的一般終結進程。 它也會略過使用函數指定的任何特殊處理 [atexit](../c-runtime-library/reference/atexit.md) 。

## <a name="no-locatexit-function"></a>atexit 函式

您 [atexit](../c-runtime-library/reference/atexit.md) 可以使用函數來指定在程式終止之前執行的動作。 在呼叫之前初始化的全域靜態物件，在 **atexit** 執行處理函式之前都已損毀 exit 。

## <a name="no-locreturn-statement-in-no-locmain"></a>return 中的語句 main

發出的 [return](return-statement-cpp.md) 語句在 `main` 功能上相當於呼叫函式 `exit` 。 請考慮下列範例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit` **`return`** 上述範例中的和語句的功能相同。 不過，c + + 需要具有值以外之類型的函式 return **`void`** return 。 **`return`** 語句可讓您 return 使用的值 `main` 。

## <a name="destruction-of-static-objects"></a>靜態物件的銷毀

當您 `exit` 從呼叫或執行 **`return`** 語句時 `main` ，靜態物件會在呼叫之後，以其初始化 (的反向順序終結（如果有的話） `atexit`) 。 下列範例將示範這類初始化和清除如何運作：

### <a name="example"></a>範例

在下列範例中， `sd1` `sd2` 會在進入之前建立和初始化靜態物件和 `main` 。 使用語句終止這個程式之後 **`return`** ，第一個 `sd2` 就會終結，然後是 `sd1` 。 `ShowData` 類別的解構函式會關閉與這些靜態物件相關聯的檔案 

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

另一種撰寫這個程式碼的方式，是使用區塊範圍宣告 `ShowData` 物件，讓物件能夠在超出範圍時終結：

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>另請參閱

[main 函數和命令列引數](main-function-command-line-args.md)
