---
title: "time_get_byname 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- time_get_byname
- xloctime/std::time_get_byname
dev_langs:
- C++
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
caps.latest.revision: 25
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 609bf85c8d56172f9498997e83740cf9620798dc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="timegetbyname-class"></a>time_get_byname 類別
衍生的樣板類別描述可做為類型 `time_get`\<CharType, InputIterator> 的地區設定 facet 的物件。  
  
## <a name="syntax"></a>語法  
  
```
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```  
  
#### <a name="parameters"></a>參數  
 `_Locname`  
 具名地區設定。  
  
 `_Refs`  
 初始參考計數。  
  
## <a name="requirements"></a>需求  
 其行為取決於具名地區設定 `_Locname`。 每個建構函式會以 [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator>( `_Refs`) 初始化其基底物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




