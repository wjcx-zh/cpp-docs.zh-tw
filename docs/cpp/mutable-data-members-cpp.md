---
title: 可變動的資料成員 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65d2fc42021a01a1260b57f9516e53c439c8e604
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943000"
---
# <a name="mutable-data-members-c"></a>可變動的資料成員 (C++)
這個關鍵字只能套用至非靜態和非常數類別的資料成員。 如果資料成員宣告**可變**，則將值指派給這個資料成員，從**const**成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>備註  
 例如，下列程式碼會編譯無誤因為`m_accessCount`被宣告為**可變動**，，因此可以藉由修改`GetFlag`即使`GetFlag`為 const 成員函式。  
  
```cpp 
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)