---
title: "C++ 的全域常數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常數, 全域"
  - "全域常數"
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 的全域常數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C\+\+ 全域常數具有靜態連結。  這點與 C 不同。  如果您嘗試在多個檔案中使用 C\+\+ 的全域常數，就會發生無法在外部之程式庫中找到或連結所需之資料型別或函式的錯誤。  編譯器最佳化時會排除全域常數，不會為變數保留空間。  
  
 解決這項錯誤的方法之一就是：在標頭檔中包含該 const 的初始化設定，必要時，並將該標頭檔包含在您的 CPP 檔中，將它當成函式原型。  另一種可行方法是將變數設成非常數，並用常數參考來評估它。  
  
 下列範例會產生 C2019：  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 然後，  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## 請參閱  
 [連結器工具錯誤 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)