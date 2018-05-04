---
title: 可變動的資料成員 （c + +） |Microsoft 文件
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
ms.openlocfilehash: e7dd639cbf1ef076dee6e447f317533bf12dae10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mutable-data-members-c"></a>可變動的資料成員 (C++)
這個關鍵字只能套用至非靜態和非常數類別的資料成員。 如果資料成員宣告`mutable`，則將值指派給這個資料成員，從**const**成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>備註  
 例如，下列程式碼會在沒有錯誤的情況下完成編譯，因為 `m_accessCount` 已宣告為 `mutable`，因此，即使 `GetFlag` 是常數成員函式，`GetFlag` 也可以進行修改。  
  
```  
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