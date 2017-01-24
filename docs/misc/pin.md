---
title: "__pin | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pin 指標，__pin 關鍵字"
  - "Unmanaged 類型"
  - "__pin 關鍵字"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
**注意**：本主題只適用於 Managed Extensions for C\+\+ 第 1 版。 這個語法只可用於維護第 1 版的程式碼。 請參閱 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md) 如需新語法中使用的相同功能。  
  
 防止 Common Language Runtime 在記憶體回收期間移動 Managed 類別的物件或內嵌物件。  
  
## 語法  
  
```  
  
__pin   
identifier  
  
```  
  
## 備註  
 `__pin` 關鍵字會宣告 Managed 類別之物件或內嵌物件的指標，防止 Common Language Runtime 在記憶體回收期間移動該物件。 利用這種方式將 Managed 類別的位址傳遞至 Unmanaged 函式會很有用，因為位址不會在解析 Unmanaged 函式呼叫時意外變更。  
  
 Pin 指標在其語彙範圍內會保持有效。 只要 Pin 指標超出範圍，物件就不再視為固定 \(除非有其他指向該物件或在該物件內的 Pin 指標存在\)。  
  
 MSIL 沒有「區塊範圍」的概念，因為所有區域變數都位於函式範圍內。 為了讓系統得知固定不再有效，編譯器會產生程式碼，將 NULL 指派至 Pin 指標。 如果您需要取消固定物件，但不離開區塊，您也可以這樣做。  
  
 將 Pin 指標轉換成 Unmanaged 指標後，就不應該在物件不再固定 \(Pin 指標超出範圍\) 之後繼續使用這個 Unmanaged 指標。 與 gc 指標不同的是，Pin 指標可以轉換成 nogc，也就是 Unmanaged 指標。 不過，使用者必須負責在使用 Unmanaged 指標時維護固定動作。  
  
 若您使用 Pin 指標取得變數的位址，則不應該在 Pin 指標超出範圍後使用該位址。  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 下列範例將示範正確的行為：  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## 範例  
 在下列範例中，`pG` 所指向的物件會固定，直到它超出範圍：  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## 輸出  
  
```  
1  
```