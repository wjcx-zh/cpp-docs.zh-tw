---
title: "const 和 volatile 指標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: bebd757f304de2377ab2337e5b41a577a2b492b6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="const-and-volatile-pointers"></a>const 和 volatile 指標
[Const](../cpp/const-cpp.md)和[volatile](../cpp/volatile-cpp.md)關鍵字會改變指標的處理方式。 **Const**關鍵字會指定在初始化之後，無法修改指標; 指標受到保護以避免之後修改。  
  
 `volatile` 關鍵字指定與其後的名稱相關聯的值，可以透過使用者應用程式以外的動作進行修改。 因此，若是要在可由多個程序或全域資料區域存取的共用記憶體中宣告物件，以便與中斷服務常式進行通訊，`volatile` 關鍵字會非常有用。  
  
 當名稱宣告為 `volatile` 時，編譯器會在程式每次存取時，從記憶體重新載入值。 這將可大幅減少進行最佳化的次數。 不過，當物件的狀態可能遭到意外變更時，它仍是確保可預測程式效能的唯一方式。  
  
 若要宣告為指標所指向的物件**const**或`volatile`，使用表單的宣告：  
  
```  
const char *cpch;  
volatile char *vpch;  
```  
  
 若要宣告指標的值 — 也就是儲存在指標的實際位址，做為**const**或`volatile`，使用表單的宣告：  
  
```  
char * const pchc;  
char * volatile pchv;  
```  
  
 C + + 語言會防止指派，允許修改物件或指標宣告為**const**。 這類指派會移除用來宣告物件或指標的資訊，因此違反了原始宣告的用意。 請考慮下列宣告：  
  
```  
const char cch = 'A';  
char ch = 'B';  
```  
  
 以上述兩個物件的宣告 (`cch`，型別**const char**，和`ch`，型別**char)**，下列宣告/初始化是有效：  
  
```  
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 下列宣告/初始化是錯誤的。  
  
```  
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 `pch2` 的宣告會宣告一項指標，但是常數物件可能會透過該指標而遭到修改，因此不允許此宣告。 `pch3` 的宣告中將 `pointer` 指定為常數而非物件，因此基於相同原因，也不允許 `pch2` 宣告。  
  
 下列八個指派顯示透過指標進行的指派，以及變更上述宣告的指標值；現在，我們可以假設透過 `pch1` 進行 `pch8` 的初始化是正確的。  
  
```  
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 指標宣告為`volatile`，或為混合**const**和`volatile`，遵守相同的規則。  
  
 指標**const**物件通常用在函式宣告，如下所示：  
  
```  
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 上述陳述式會宣告函式， [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中有兩的三個引數的類型指標`char`。 因為引數傳址方式傳遞而不依據值、 函式會是可用來修改這兩`strDestination`和`strSource`如果`strSource`未宣告為**const**。 宣告`strSource`為**const**確保呼叫端`strSource`式呼叫的函式不能變更。  
  
> [!NOTE]
>  因為沒有標準轉換轉換*typename* ** \* **至**const** *typename* ** \***，它是合法的類型引數傳遞**char \* **至[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)。 不過，反向並不成立沒有隱含轉換存在移除**const**從物件或指標的屬性。  
  
 A **const**給定類型的指標可以指派給相同類型的指標。 不過，指標的不是**const**無法指派給**const**指標。 下列程式碼顯示正確和不正確的指派：  
  
```  
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 下列範例顯示在您有一個指標指向物件的指標時，如何將物件宣告為常數。  
  
```  
// const_pointer2.cpp  
struct X {  
   X(int i) : m_i(i) { }  
   int m_i;  
};  
  
int main() {  
   // correct  
   const X cx(10);  
   const X * pcx = &cx;  
   const X ** ppcx = &pcx;  
  
   // also correct  
   X const cx2(20);  
   X const * pcx2 = &cx2;  
   X const ** ppcx2 = &pcx2;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [指標](../cpp/pointers-cpp.md)
