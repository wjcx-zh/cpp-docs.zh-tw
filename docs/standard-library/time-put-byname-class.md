---
title: "time_put_byname 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xloctime/std::time_put_byname
dev_langs:
- C++
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: ba50414643d430798912e6a7a25d3fe9c49c1b9a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="timeputbyname-class"></a>time_put_byname 類別
衍生的樣板類別描述可做為類型 `time_put`\< CharType, OutputIterator > 的地區設定 facet 的物件。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```  
  
#### <a name="parameters"></a>參數  
 `_Locname`  
 地區設定名稱。  
  
 `_Refs`  
 初始參考計數。  
  
## <a name="remarks"></a>備註  
 其行為取決於[具名](../standard-library/locale-class.md#name)地區設定 `_Locname`。 每個建構函式會以 [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator>( `_Refs`) 初始化其基底物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




