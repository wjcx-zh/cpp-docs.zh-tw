---
title: "final 規範 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c9f0a638707466778e75a3eabfe838c84b0355d7
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="final-specifier"></a>final 規範
您可以使用 `final` 關鍵字指定無法在衍生類別中覆寫的虛擬函式。 您也可以用它來指定無法被繼承的類別。  
  
## <a name="syntax"></a>語法  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>備註  
 `final` 具有內容相關性，而且只有在函式宣告或類別名稱之後使用時才具有特殊意義，否則它不是保留的關鍵字。  
  
 當 `final` 用於類別宣告時，`base-classes` 是宣告中的選擇性部分。  
  
## <a name="example"></a>範例  
 下列範例會使用 `final` 關鍵字來指定無法覆寫的虛擬函式。  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 如需如何指定可覆寫成員函式的資訊，請參閱[覆寫規範](../cpp/override-specifier.md)。  
  
 下一個範例會使用 `final` 關鍵字來指定無法被繼承的類別。  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [override 規範](../cpp/override-specifier.md)
