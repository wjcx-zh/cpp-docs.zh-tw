---
title: "複合陳述式 （區塊） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9dc28fde0ab2cf5b21771347554d0c664b7f462d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="compound-statements-blocks"></a>複合陳述式 (區塊)
複合陳述式包含大括號括住的零或多個陳述式 (**{}**)。 複合陳述式可以在必須有陳述式的任何位置使用。 複合陳述式通常稱為「區塊」(Block)。  
  
## <a name="syntax"></a>語法  
  
```  
  
{ [ statement-list ] }  
```  
  
## <a name="remarks"></a>備註  
 下列範例使用複合陳述式為*陳述式*屬於**如果**陳述式 (請參閱[if 陳述式](../cpp/if-else-statement-cpp.md)語法的詳細資料):  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
{
    Balance -= Amount;  
}
```  
  
> [!NOTE]
>  由於宣告是陳述式，宣告可以是其中一個陳述式中*陳述式清單*。 因此，在複合陳述式內宣告，但未明確宣告為靜態的名稱，會具有區域範圍和 (為物件時) 存留期。 請參閱[範圍](../cpp/scope-visual-cpp.md)具有本機領域名稱的處理方式的詳細資料。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 陳述式概觀](../cpp/overview-of-cpp-statements.md)
