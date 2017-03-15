---
title: "const 和 volatile 指標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const 關鍵字 [C++], volatile 指標"
  - "指標, 和 const"
  - "指標, 和 volatile"
  - "volatile 關鍵字 [C++], 和指標"
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# const 和 volatile 指標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[const](../cpp/const-cpp.md) 和 [volatile](../cpp/volatile-cpp.md) 關鍵字會改變指標的處理方式。  **const** 關鍵字會指定指標在初始化之後無法加以修改；因此指標此後可受到保護而不會遭到修改。  
  
 `volatile` 關鍵字指定與其後的名稱相關聯的值，可以透過使用者應用程式以外的動作進行修改。  因此，若是要在可由多個程序或全域資料區域存取的共用記憶體中宣告物件，以便與中斷服務常式進行通訊，`volatile` 關鍵字會非常有用。  
  
 當名稱宣告為 `volatile` 時，編譯器會在程式每次存取時，從記憶體重新載入值。  這將可大幅減少進行最佳化的次數。  不過，當物件的狀態可能遭到意外變更時，它仍是確保可預測程式效能的唯一方式。  
  
 若要將由指標所指的物件宣告為 **const** 或 `volatile`，請使用下列格式進行宣告：  
  
```  
const char *cpch;  
volatile char *vpch;  
```  
  
 若要將指標的值 \(也就是指標中儲存的實際位址\) 宣告為**const** 或 `volatile`，請使用下列格式進行宣告：  
  
```  
char * const pchc;  
char * volatile pchv;  
```  
  
 C\+\+ 語言會避免允許修改物件或宣告為 **const** 之指標的任何指派。  這類指派會移除用來宣告物件或指標的資訊，因此違反了原始宣告的用意。  請考慮下列宣告：  
  
```  
const char cch = 'A';  
char ch = 'B';  
```  
  
 對於上述宣告中的兩個物件 \(類型為 **const char** 的 `cch`，以及類型為 **char** 的 `ch`\)，下列宣告\/初始化是有效的：  
  
```  
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 下列宣告\/初始化是錯誤的。  
  
```  
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 `pch2` 的宣告會宣告一項指標，但是常數物件可能會透過該指標而遭到修改，因此不允許此宣告。  `pch3` 的宣告中將 `pointer` 指定為常數而非物件，因此基於相同原因，也不允許 `pch2` 宣告。  
  
 下列八個指派顯示透過指標進行的指派，以及變更上述宣告的指標值；現在，我們可以假設透過 `pch8` 進行 `pch1` 的初始化是正確的。  
  
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
  
 宣告為 `volatile`，或者宣告為混合 **const** 和 `volatile` 的指標會遵守相同的規則。  
  
 **const** 物件的指標通常會在函式宣告中使用，如下所示：  
  
```  
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 上述陳述式宣告了一個函式 [strcpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)，其中三個引數中有兩個引數為 `char` 類型的指標。  由於引數是經由傳址方式而不是傳值方式傳遞，因此若 `strSource` 不是宣告為 **const**，則可允許函式修改 `strDestination` 和 `strSource`。  `strSource` 宣告為 **const**，確保呼叫端 `strSource` 無法藉由所呼叫的函式加以變更。  
  
> [!NOTE]
>  由於已進行從 *typename* **\*** 轉換為 **const** *typename* **\*** 的標準轉換，因此它可以將類型 **char \*** 的引數傳遞至 [strcpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)。  不過，反向操作則不可行，因為其中並不存在將 **const** 屬性從物件或指標移除的隱含轉換。  
  
 已指定類型的 **const** 指標可以指派給相同類型的指標。  不過，不是 **const** 的指標不可以指派給 **const** 指標。  下列程式碼顯示正確和不正確的指派：  
  
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
  
## 請參閱  
 [指標](../cpp/pointers-cpp.md)