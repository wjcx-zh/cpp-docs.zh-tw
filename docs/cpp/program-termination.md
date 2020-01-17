---
title: C++程式終止
description: 說明 exit C++語言程式的方式。
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
ms.openlocfilehash: f83c9d5da5b0a1127603a97fd7946e9cca43a7a5
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123951"
---
# <a name="c-program-termination"></a>C++程式終止

在C++中，您可以透過下列方式 exit 程式：

- 呼叫[exit](exit-function.md)函式。
- 呼叫[abort](abort-function.md)函式。
- 從 `main`執行[return](return-statement-cpp.md)語句。

## <a name="opno-locexit-function"></a>exit 函式

\<> stdlib.h> 中宣告的[exit](../c-runtime-library/reference/exit-exit-exit.md)函式會終止C++程式。 當做引數提供給 `exit` 的值，會以程式的 return 碼或 exit 代碼的形式傳回作業系統。 依照慣例，return 的代碼為零，表示程式已順利完成。 您可以使用常數 EXIT_FAILURE 和 EXIT_SUCCESS （也是在 \<> stdlib.h> 中定義），以表示程式的成功或失敗。

從 `main` 函式發出 **return** 語句，相當於使用 return 值做為其引數呼叫 `exit` 函數。

## <a name="opno-locabort-function"></a>abort 函式

[abort](../c-runtime-library/reference/abort.md)函式也會在標準 include 檔中宣告 \<stdlib.h> >，會終止C++程式。 `exit` 和 `abort` 之間的差異在於 `exit` 允許執行C++執行時間終止處理（將會呼叫全域物件的析構函數），而 `abort` 會立即終止程式。 `abort` 函式會針對初始化的全域靜態物件略過正常的析構進程。 它也會略過使用[atexit](../c-runtime-library/reference/atexit.md)函數指定的任何特殊處理。

## <a name="opno-locatexit-function"></a>atexit 函式

使用[atexit](../c-runtime-library/reference/atexit.md)函式來指定程式終止之前執行的動作。 在執行 exit處理函式之前，不會先對 **atexit** 呼叫之前初始化的全域靜態物件。

## <a name="opno-locreturn-statement-in-opno-locmain"></a>main 中的 return 語句

從 `main` 發出[return](return-statement-cpp.md)語句，在功能上相當於呼叫 `exit` 函數。 參考下列範例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

上述範例中的 `exit` 和 **return** 語句的功能完全相同。 不過， C++需要 **void** 以外的 return 類型 return 值的函式。 **return** 語句可讓您 return `main`中的值。

## <a name="destruction-of-static-objects"></a>靜態物件的析構

當您呼叫 `exit` 或從 `main`執行 **return** 語句時，靜態物件會以其初始化的反向順序終結（如果有，則會在呼叫 `atexit` 之後）。 下列範例將示範這類初始化和清除如何運作：

### <a name="example"></a>範例

在下列範例中，`sd1` 和 `sd2` 的靜態物件會在進入 `main`之前建立並初始化。 在此程式使用 **return** 語句終止之後，先 `sd2`，然後再 `sd1`。 `ShowData` 類別的解構函式會關閉與這些靜態物件相關聯的檔案

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

## <a name="see-also"></a>請參閱

[main 函式和命令列引數](main-function-command-line-args.md)
