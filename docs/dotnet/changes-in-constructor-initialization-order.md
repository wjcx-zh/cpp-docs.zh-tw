---
title: "建構函式初始設定順序的變更 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "建構函式, C++"
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建構函式初始設定順序的變更
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，類別建構函式的初始設定順序已變更。  
  
## 建構函式初始設定順序的比較  
 在 Managed Extensions for C\+\+ 中，建構函式初始設定的進行順序如下：  
  
1.  叫用基底類別的建構函式 \(如果有的話\)。  
  
2.  評估類別的初始設定清單。  
  
3.  執行類別建構函式的程式碼主體。  
  
 這個執行順序與原生 C\+\+ 程式設計遵循相同的慣例。  新的 Visual C\+\+ 語言規定 CLR 類別的執行順序如下：  
  
1.  評估類別的初始設定清單。  
  
2.  叫用基底類別的建構函式 \(如果有的話\)。  
  
3.  執行類別建構函式的程式碼主體。  
  
 請注意，這項變更只適用於 CLR 類別，[!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中的原生類別仍然遵循以前的慣例。  不論兩者哪一種狀況，這些規則都會向上串聯，處理指定類別的整個階層鏈結。  
  
 請看看下列使用 Managed Extensions for C\+\+ 的程式碼範例：  
  
```  
__gc class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
__gc class B : public A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 遵循上述規定的建構函式初始設定順序，在建立 `B` 的新執行個體時，執行順序應該如下：  
  
1.  叫用基底類別 `A` 的建構函式。  `_n` 成員會初始化成為 `1`。  
  
2.  評估類別 `B` 的初始設定清單。  `_m` 成員會初始化成為 `1`。  
  
3.  執行類別 `B` 的程式碼主體。  
  
 現在看看使用新 Visual C\+\+ 語法的同一個程式碼：  
  
```  
ref class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
ref class B : A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 在新語法下，建構類別 `B` 之新執行個體時的執行順序：  
  
1.  評估類別 `B` 的初始設定清單。  `_m` 成員會初始化成為 `0` \(`0` 是 `_m` 類別成員未初始化的值\)。  
  
2.  叫用基底類別 `A` 的建構函式。  `_n` 成員會初始化成為 `1`。  
  
3.  執行類別 `B` 的程式碼主體。  
  
 請注意，這些程式碼範例的語法雖類似，卻產生出不同的結果。  類別 `B` 的建構函式須依靠基底類別 `A` 的值來初始化它的成員，  但是類別 `A` 的建構函式卻尚未叫用。  當繼承類別取決於基底類別建構函式中即將進行的記憶體或資源配置時，這樣的相依性可能特別危險。  
  
## 從 Managed Extensions for C\+\+ 移至 Visual C\+\+ 2010 的意義  
 在許多情況下，程式設計師應該不會察覺類別建構函式執行順序的變更，因為基底類別並不了解繼承類別的行為。  但是如這些程式碼範例所示，當繼承類別的初始設定清單取決於基底類別成員的值時，繼承類別的建構函式可能受到嚴重影響。  當您將程式碼從 Managed Extensions for C\+\+ 移到新語法時，請考慮將這類建構函式移到類別建構函式主體中，就可以保證它的執行會最後發生。  
  
## 請參閱  
 [Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [建構函式](../cpp/constructors-cpp.md)   
 [建構函式初始設定式](../misc/constructor-initializers.md)