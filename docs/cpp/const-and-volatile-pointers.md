---
title: const 和 volatile 指標 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b63e2da6286e6a8e10ecf29a37ec9d74e9f1dfc0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942668"
---
# <a name="const-and-volatile-pointers"></a>const 和 volatile 指標
[Const](../cpp/const-cpp.md)並[volatile](../cpp/volatile-cpp.md)關鍵字會改變指標的處理方式。 **Const**關鍵字會指定在初始設定之後，無法修改指標; 指標防止之後修改。  
  
 **Volatile**關鍵字可讓您指定的使用者應用程式以外的動作可以修改後面的名稱與相關聯的值。 因此， **volatile**關鍵字會宣告可以存取多個處理程序或全域資料區域與中斷服務常式進行通訊的共用記憶體中的物件非常有用。  
  
 當名稱宣告為**volatile**，編譯器會重新載入記憶體中的值每次程式所存取時。 這將可大幅減少進行最佳化的次數。 不過，當物件的狀態可能遭到意外變更時，它仍是確保可預測程式效能的唯一方式。  
  
 若要宣告為指標所指向的物件**const**或**volatile**，使用格式進行宣告：  
  
```cpp 
const char *cpch;  
volatile char *vpch;  
```  
  
 若要宣告指標的值 — 也就是在指標中儲存的實際位址，作為**const**或**volatile**，使用格式進行宣告：  
  
```cpp 
char * const pchc;  
char * volatile pchv;  
```  
  
 C + + 語言可避免允許修改物件的指派或指標宣告為**const**。 這類指派會移除用來宣告物件或指標的資訊，因此違反了原始宣告的用意。 請考慮下列宣告：  
  
```cpp 
const char cch = 'A';  
char ch = 'B';  
```  
  
 對於上述宣告中的兩個物件 (`cch`，型別的**const char**，以及`ch`，型別的**char)**，下列宣告/初始化是有效：  
  
```cpp 
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 下列宣告/初始化是錯誤的。  
  
```cpp 
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 `pch2` 的宣告會宣告一項指標，但是常數物件可能會透過該指標而遭到修改，因此不允許此宣告。 宣告`pch3`指定**指標**是常數、 非物件，宣告不允許基於相同原因`pch2`宣告不允許。  
  
 下列八個指派顯示透過指標進行的指派，以及變更上述宣告的指標值；現在，我們可以假設透過 `pch1` 進行 `pch8` 的初始化是正確的。  
  
```cpp 
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 指標宣告為**volatile**，或為混合**const**並**volatile**，必須遵守相同的規則。  
  
 指標**const**物件通常用在函式宣告，如下所示：  
  
```cpp 
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 前面的陳述式會宣告函式[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中三個引數的兩個屬於型別指標**char**。 因為引數傳址方式傳遞，而且不值，則可允許函式修改`strDestination`並`strSource`如果`strSource`不是宣告為**const**。 Deklarace`strSource`做為**const**可確保呼叫端`strSource`呼叫的函式無法變更。  
  
> [!NOTE]
>  因為沒有標準轉換轉換*typename* **\*** 來**const** *typename*  **\***，它是合法的類型引數傳遞**char \*** 來[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)。 不過，並非反之亦然;移除存在的任何隱含的轉換**const**從物件或指標的屬性。  
  
 A **const**給定類型的指標可以指派給相同類型的指標。 不過，指標的不是**const**無法指派給**const**指標。 下列程式碼顯示正確和不正確的指派：  
  
```cpp 
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 下列範例顯示在您有一個指標指向物件的指標時，如何將物件宣告為常數。  
  
```cpp 
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