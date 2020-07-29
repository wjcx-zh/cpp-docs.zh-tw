---
title: 標記陳述式
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: a10d071e46c79f49abf7e3eba498fae0487ccdc7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213355"
---
# <a name="labeled-statements"></a>標記陳述式

標籤可用來將程式控制權直接轉移給指定的陳述式。

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

標籤的範圍宣告該標籤所在的整個函式。

## <a name="remarks"></a>備註

標記陳述式可分三種類型。 這三種類型全都使用冒號分隔某種類型的標籤與陳述式。 case 和 default 標籤為 case 陳述式所特有。

```cpp
#include <iostream>
using namespace std;

void test_label(int x) {

    if (x == 1){
        goto label1;
    }
    goto label2;

label1:
    cout << "in label1" << endl;
    return;

label2:
    cout << "in label2" << endl;
    return;
}

int main() {
    test_label(1);  // in label1
    test_label(2);  // in label2
}
```

**goto 陳述式**

來來源程式中*識別碼*標籤的外觀會宣告標籤。 只有[goto](../cpp/goto-statement-cpp.md)語句可以將控制項傳輸至*識別碼*標籤。 下列程式碼片段說明 **`goto`** 語句和*識別碼*標籤的使用：

標籤不會單獨顯示，而是必須附加至陳述式。 如果需要單獨使用標籤，請在標籤之後放置一個 null 陳述式。

標籤具有函式範圍，而且不能在函式中宣告。 然而，在不同的函式中可以使用相同名稱做為標籤。

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
}

//Output: At Test2 label.
```

**case 陳述式**

出現在關鍵字後面的標籤 **`case`** 也不能出現在 **`switch`** 語句之外。 （此限制也適用于 **`default`** 關鍵字）。下列程式碼片段會顯示標籤的正確用法 **`case`** ：

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );
      EndPaint( hWnd, &ps );
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-case-statement"></a>case 陳述式中的標籤

出現在關鍵字後面的標籤 **`case`** 也不能出現在 **`switch`** 語句之外。 （此限制也適用于 **`default`** 關鍵字）。下列程式碼片段會顯示標籤的正確用法 **`case`** ：

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      // Obtain a handle to the device context.
      // BeginPaint will send WM_ERASEBKGND if appropriate.

      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );

      // Inform Windows that painting is complete.

      EndPaint( hWnd, &ps );
      break;

   case WM_CLOSE:
      // Close this window and all child windows.

      KillTimer( hWnd, TIMER1 );
      DestroyWindow( hWnd );
      if ( hWnd == hWndMain )
         PostQuitMessage( 0 );  // Quit the application.
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-goto-statement"></a>goto 陳述式中的標籤

來來源程式中*識別碼*標籤的外觀會宣告標籤。 只有[goto](../cpp/goto-statement-cpp.md)語句可以將控制項傳輸至*識別碼*標籤。 下列程式碼片段說明 **`goto`** 語句和*識別碼*標籤的使用：

標籤不會單獨顯示，而是必須附加至陳述式。 如果需要單獨使用標籤，請在標籤之後放置一個 null 陳述式。

標籤具有函式範圍，而且不能在函式中宣告。 然而，在不同的函式中可以使用相同名稱做為標籤。

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
// At Test2 label.
}
```

## <a name="see-also"></a>另請參閱

[C + + 語句總覽](../cpp/overview-of-cpp-statements.md)<br/>
[switch 語句（c + +）](../cpp/switch-statement-cpp.md)
