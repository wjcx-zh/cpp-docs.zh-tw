---
title: "建構函式初始設定順序變更 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 499855ec5052c039e007df8348db094aee356411
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-constructor-initialization-order"></a>建構函式初始設定順序的變更
類別建構函式的初始化順序已從 Managed Extensions for c + + Visual c + +。  
  
## <a name="comparison-of-constructor-initialization-order"></a>建構函式初始設定順序的比較  
 在 Managed Extensions for c + +，建構函式初始化發生順序如下：  
  
1.  建構函式的基底類別中，如果有的話，會叫用。  
  
2.  會評估初始化清單中的類別。  
  
3.  執行程式碼主體的類別建構函式。  
  
 執行此順序會遵循相同的慣例，與原生 c + + 程式設計。 新的 Visual c + + 語言所給定之下列的執行順序的 CLR 類別：  
  
1.  會評估初始化清單中的類別。  
  
2.  建構函式的基底類別中，如果有的話，會叫用。  
  
3.  執行程式碼主體的類別建構函式。  
  
 請注意這項變更只適用於 CLR 類別。Visual c + + 中的原生類別仍然會遵照先前的慣例。 在這兩種情況下，這些規則都會向上串聯整個階層的鏈結提供的類別。  
  
 請考慮下列程式碼範例使用 Managed Extensions for c + +:  
  
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
  
 上述建構函式初始化順序規定，我們應該會看到下列順序執行時是新的類別的執行個體`B`建構：  
  
1.  基底類別的建構函式`A`叫用。 `_n`成員初始化為`1`。  
  
2.  類別初始設定清單`B`評估。 `_m`成員初始化為`1`。  
  
3.  類別的程式碼主體`B`執行。  
  
 現在請考慮在新的 Visual c + + 語法相同的程式碼：  
  
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
  
 當新的執行順序類別的執行個體`B`建構在新語法是：  
  
1.  類別初始設定清單`B`評估。 `_m`成員初始化為`0`(`0`是未初始化的值`_m`類別成員)。  
  
2.  基底類別的建構函式`A`叫用。 `_n`成員初始化為`1`。  
  
3.  類別的程式碼主體`B`執行。  
  
 請注意類似的語法會產生不同的結果，如下列程式碼範例。 類別建構函式`B`取決於基底類別的值`A`初始化其成員。 不過，類別的建構函式`A`有尚未被叫用。 繼承的類別取決於基底類別建構函式中發生的記憶體或資源配置時，這類相依性可能會特別危險。  
  
## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>此意義從 Managed Extensions for c + + 移至 Visual c + + 2010年  
 在許多情況下類別建構函式的執行順序的變更應該是透明程式設計人員因為基底類別有沒有繼承的類別行為的概念。 不過，如下列程式碼範例所示，繼承類別的建構函式可能會大幅影響時的初始設定清單的值相依於基底類別成員。 當您移動您的程式碼從 Managed Extensions for c + + 的新語法時，請考慮將這類建構移至類別建構函式主體執行都一定時間。  
  
## <a name="see-also"></a>請參閱  
 [Managed 類型 (C + + CL)](../dotnet/managed-types-cpp-cl.md)   
 [建構函式](../cpp/constructors-cpp.md)   
 