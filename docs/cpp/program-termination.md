---
title: C + + 程式終止
description: '描述 :::no-loc(exit)::: c + + 語言程式的方式。'
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- :::no-loc(exit):::ing applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- ':::no-loc(exit):::'
- ':::no-loc(abort):::'
- ':::no-loc(return):::'
- ':::no-loc(main):::'
- ':::no-loc(atexit):::'
- ':::no-loc(void):::'
ms.openlocfilehash: 216aef5dbe8d110f9d75d43b5009b89fc5bfda51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227175"
---
# <a name="c-program-termination"></a>C + + 程式終止

在 c + + 中，您可以 :::no-loc(exit)::: 使用下列方式來執行程式：

- 呼叫函式 [:::no-loc(exit):::](:::no-loc(exit):::-function.md) 。
- 呼叫函式 [:::no-loc(abort):::](:::no-loc(abort):::-function.md) 。
- 從執行 [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) 語句 `:::no-loc(main):::` 。

## <a name="no-locexit-function"></a>:::no-loc(exit)::: 函式

在中宣告的函式會 [:::no-loc(exit):::](../c-runtime-library/reference/:::no-loc(exit):::-:::no-loc(exit):::-:::no-loc(exit):::.md) \<stdlib.h> 終止 c + + 程式。 當做引數提供給作業系統的值 `:::no-loc(exit):::` ，會與 :::no-loc(return)::: 程式的程式 :::no-loc(return)::: 代碼或 :::no-loc(exit)::: 代碼相同。 依照慣例， :::no-loc(return)::: 代碼為零表示程式已順利完成。 您可以使用 EXIT_FAILURE 和 EXIT_SUCCESS 的常數，也就是在中定義 \<stdlib.h> ，以指出程式的成功或失敗。

從函式發出 **`:::no-loc(return):::`** 語句 `:::no-loc(main):::` 相當於呼叫 `:::no-loc(exit):::` 具有 :::no-loc(return)::: 值做為其引數的函式。

## <a name="no-locabort-function"></a>:::no-loc(abort)::: 函式

函式 [:::no-loc(abort):::](../c-runtime-library/reference/:::no-loc(abort):::.md) （也在標準 include 檔中宣告 \<stdlib.h> ）會終止 c + + 程式。 和之間的差異在於 `:::no-loc(exit):::` `:::no-loc(abort):::` `:::no-loc(exit):::` 允許執行 c + + 執行時間終止處理（將會呼叫全域物件的析構函數），而會 `:::no-loc(abort):::` 立即終止程式。 函式會 `:::no-loc(abort):::` 針對初始化的全域靜態物件略過正常的析構進程。 它也會略過使用函數指定的任何特殊處理 [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) 。

## <a name="no-locatexit-function"></a>:::no-loc(atexit)::: 函式

使用 [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) 函數來指定程式終止之前執行的動作。 在 **:::no-loc(atexit):::** 執行處理函式之前，不會先終結在呼叫之前初始化的全域靜態物件 :::no-loc(exit)::: 。

## <a name="no-locreturn-statement-in-no-locmain"></a>:::no-loc(return):::中的語句:::no-loc(main):::

從發出 [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) 語句的 `:::no-loc(main):::` 功能相當於呼叫 `:::no-loc(exit):::` 函數。 請考慮下列範例：

```cpp
// :::no-loc(return):::_statement.cpp
#include <stdlib.h>
int :::no-loc(main):::()
{
    :::no-loc(exit):::( 3 );
    :::no-loc(return)::: 3;
}
```

`:::no-loc(exit):::` **`:::no-loc(return):::`** 前述範例中的和語句的功能相同。 不過，c + + 需要具有值以外之類型的函式 :::no-loc(return)::: **`:::no-loc(void):::`** :::no-loc(return)::: 。 **`:::no-loc(return):::`** 語句可讓您 :::no-loc(return)::: 使用的值 `:::no-loc(main):::` 。

## <a name="destruction-of-static-objects"></a>靜態物件的析構

當您 `:::no-loc(exit):::` 從呼叫或執行 **`:::no-loc(return):::`** 語句時 `:::no-loc(main):::` ，靜態物件會以其初始化的反向順序終結（ `:::no-loc(atexit):::` 如果有的話）。 下列範例將示範這類初始化和清除如何運作：

### <a name="example"></a>範例

在下列範例中， `sd1` `sd2` 會在進入之前建立及初始化靜態物件和 `:::no-loc(main):::` 。 在這個程式使用語句終止之後 **`:::no-loc(return):::`** ，先終結， `sd2` 然後再結束 `sd1` 。 `ShowData` 類別的解構函式會關閉與這些靜態物件相關聯的檔案 

```cpp
// using_:::no-loc(exit):::_or_:::no-loc(return):::1.cpp
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
   :::no-loc(void)::: Disp( char *szData ) {
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

int :::no-loc(main):::() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

另一種撰寫這個程式碼的方式，是使用區塊範圍宣告 `ShowData` 物件，讓物件能夠在超出範圍時終結：

```cpp
int :::no-loc(main):::() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>另請參閱

[:::no-loc(main):::函數和命令列引數](:::no-loc(main):::-function-command-line-args.md)
