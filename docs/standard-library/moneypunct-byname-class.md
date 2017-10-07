---
title: "moneypunct_byname 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::moneypunct_byname
dev_langs:
- C++
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: b13028649eeccad5fbc832098a3b070bb81dad45
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="moneypunctbyname-class"></a>moneypunct_byname 類別
衍生的範本類別，描述可作為特定地區設定 `moneypunct` facet 的物件，可用來將貨幣輸入欄位或貨幣輸出欄位格式化。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```  
  
## <a name="remarks"></a>備註  
 其行為取決於具名地區設定 `_Locname`。 每個建構函式都會以 [moneypunct](../standard-library/moneypunct-class.md#moneypunct)\<CharType, Intl>( `_Refs`) 將其基底物件初始化。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




