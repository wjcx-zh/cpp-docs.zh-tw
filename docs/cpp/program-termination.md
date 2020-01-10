---
title: C++程式終止
ms.date: 12/10/2019
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
ms.openlocfilehash: a0e86cacd951327d39296a183be5ee4fbc36fd15
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301336"
---
# <a name="c-program-termination"></a>C++程式終止

在C++中，您可以使用下列方式來結束程式：

- 呼叫[exit](exit-function.md)函式。
- 呼叫[abort](abort-function.md)函式。
- 從 `main`執行[return](return-statement-cpp.md)語句。

## <a name="exit-function"></a>exit 函式

\<stdlib.h> > 中宣告的[exit](../c-runtime-library/reference/exit-exit-exit.md)函式會終止C++程式。 當做引數提供給 `exit` 的值，會以程式的傳回碼或結束代碼的形式傳回到作業系統。 依照慣例，傳回碼為零，表示程式順利完成。 您可以使用常數 EXIT_FAILURE 和 EXIT_SUCCESS （也是在 \<> stdlib.h> 中定義），以表示程式的成功或失敗。

從 `main` 函式發出**return**語句相當於呼叫 `exit` 函數，並將傳回值當做其引數。

## <a name="abort-function"></a>abort 函式

[Abort](../c-runtime-library/reference/abort.md)函式也會在標準 include 檔中宣告 \<stdlib.h> >，會終止C++程式。 `exit` 和 `abort` 之間的差異在於 `exit` 允許執行C++執行時間終止處理（將會呼叫全域物件的析構函數），而 `abort` 會立即終止程式。 `abort` 函式會針對初始化的全域靜態物件略過正常的析構進程。 它也會略過使用[atexit](../c-runtime-library/reference/atexit.md)函數指定的任何特殊處理。

## <a name="atexit-function"></a>atexit 函式

使用[atexit](../c-runtime-library/reference/atexit.md)函數來指定程式終止之前執行的動作。 在執行結束處理函式之前，不會先終結在呼叫**atexit**之前初始化的全域靜態物件。

## <a name="return-statement-in-main"></a>main 中的 return 語句

從 `main` 發出[return](return-statement-cpp.md)語句的功能相當於呼叫 `exit` 函數。 參考下列範例：

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

上述範例中的 `exit` 和**return**語句的功能完全相同。 不過， C++要求具有**void**以外之傳回類型的函式會傳回值。 **Return**語句可讓您從 `main`傳回值。

## <a name="destruction-of-static-objects"></a>靜態物件的析構

當您呼叫 `exit` 或從 `main`執行**return**語句時，靜態物件會以其初始化的反向順序終結（如果存在，則在呼叫 `atexit` 之後）。 下列範例將示範這類初始化和清除如何運作：

### <a name="example"></a>範例

在下列範例中，`sd1` 和 `sd2` 的靜態物件會在進入 `main`之前建立並初始化。 在這個程式使用**return**語句終止之後，會先終結 `sd2`，然後再 `sd1`。 `ShowData` 類別的解構函式會關閉與這些靜態物件相關聯的檔案

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

[main：程式啟動](main-program-startup.md)