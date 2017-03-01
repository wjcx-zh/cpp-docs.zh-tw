---
title: "messages_byname 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- messages_byname
- std::messages_byname
- std.messages_byname
- xlocmes/std::messages_byname
dev_langs:
- C++
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: f72361dec79e82a5e4f531ad686978010f01450e
ms.lasthandoff: 02/24/2017

---
# <a name="messagesbyname-class"></a>messages_byname 類別
衍生的範本類別，描述可作為特定地區設定訊息 facet 的物件，可用來擷取當地語系化訊息。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```  
  
#### <a name="parameters"></a>參數  
 `_Locname`  
 具名地區設定。  
  
 `_Refs`  
 初始參考計數。  
  
## <a name="remarks"></a>備註  
 其行為取決於具名地區設定 `_Locname`。 每個建構函式都會以 [messages](../standard-library/messages-class.md#messages__messages)\<CharType>( `_Refs`) 將其基底物件初始化。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




