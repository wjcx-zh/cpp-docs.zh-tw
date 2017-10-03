---
title: "ctype_byname 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocale/std::ctype_byname
dev_langs:
- C++
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 5f57ef8eadf5ea963ef4a8b8c1eaa7b6ec48ee6d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ctypebyname-class"></a>ctype_byname 類別
衍生的範本類別，其描述的物件可以作為特定地區設定的 ctype Facet，以啟用字元分類、大小寫字元轉換，以及原生字元集和地區設定所指定字元集之間的轉換。  
  
## <a name="syntax"></a>語法  
  
```
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```  
  
## <a name="remarks"></a>備註  
 其行為取決於具名地區設定 `_Locname`。 每個建構函式皆會使用 [ctype](../standard-library/ctype-class.md)\<CharType>( `_Refs`) 或與 `ctype<char>` 對等的基底類別來初始化其基底物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




