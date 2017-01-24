---
title: "標記陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "goto"
  - "case"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "labeled 陳述式"
  - "陳述式, 已標記"
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 標記陳述式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

標籤可用來將程式控制權直接轉移給指定的陳述式。  
  
```  
identifier :  statement  
case constant-expression :  statement  
default :  statement  
```  
  
 標籤的範圍宣告該標籤所在的整個函式。  
  
## 備註  
 標記陳述式可分三種類型。  這三種類型全都使用冒號分隔某種類型的標籤與陳述式。  case 和 default 標籤為 case 陳述式所特有。  
  
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
  
 在原始程式中出現的 *identifier* 標籤會宣告一個標籤。  只有 [goto](../cpp/goto-statement-cpp.md) 陳述式可以將制權轉移到 *identifier* 標籤。  下列程式碼片段說明 `goto` 陳述式和 *identifier* 標籤的使用：  
  
 標籤不會單獨顯示，而是必須附加至陳述式。  如果需要單獨使用標籤，請在標籤之後放置一個 null 陳述式。  
  
 標籤具有函式範圍，而且不能在函式中宣告。  然而，在不同的函式中可以使用相同名稱做為標籤。  
  
```  
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
  
 出現在 **case** 關鍵字後面的標籤，不可同時出現在 `switch` 陳述式之外   \(這項限制也適用於 **default** 關鍵字\)。 下列程式碼片段將示範 **case** 標籤的正確用法：  
  
```  
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
  
## case 陳述式中的標籤  
 出現在 **case** 關鍵字後面的標籤，不可同時出現在 `switch` 陳述式之外   \(這項限制也適用於 **default** 關鍵字\)。 下列程式碼片段將示範 **case** 標籤的正確用法：  
  
```  
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
  
## goto 陳述式中的標籤  
 在原始程式中出現的 *identifier* 標籤會宣告一個標籤。  只有 [goto](../cpp/goto-statement-cpp.md) 陳述式才能將控制權轉移到 *identifier* 標籤。  下列程式碼片段說明 `goto` 陳述式和 *identifier* 標籤的使用：  
  
 標籤不會單獨顯示，而是必須附加至陳述式。  如果需要單獨使用標籤，請在標籤之後放置一個 null 陳述式。  
  
 標籤具有函式範圍，而且不能在函式中宣告。  然而，在不同的函式中可以使用相同名稱做為標籤。  
  
```  
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
  
## 請參閱  
 [C\+\+ 陳述式概觀](../cpp/overview-of-cpp-statements.md)   
 [switch 陳述式 \(C\+\+\)](../cpp/switch-statement-cpp.md)