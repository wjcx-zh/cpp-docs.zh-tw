---
title: 結束 exit 或 return
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
ms.openlocfilehash: d60084c0d07d3eeb3f49a1fea53de04d150a701b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442732"
---
# <a name="using-exit-or-return"></a>結束 exit 或 return

當您呼叫**結束**或執行**會傳回**陳述式從`main`，靜態物件會在其初始化的反向順序終結。 下列範例將示範這類初始化和清除如何運作：

## <a name="example"></a>範例

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

在上述範例中，靜態物件 `sd1` 和 `sd2` 會在進入 `main` 之前建立並初始化。 此程式會終止使用之後**會傳回**陳述式中，第一個`sd2`終結，然後`sd1`。 `ShowData` 類別的解構函式會關閉與這些靜態物件相關聯的檔案 

另一種撰寫這個程式碼的方式，是使用區塊範圍宣告 `ShowData` 物件，讓物件能夠在超出範圍時終結：

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>另請參閱

[其他終止考量](../cpp/additional-termination-considerations.md)