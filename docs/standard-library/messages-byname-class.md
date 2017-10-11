---
title: "messages_byname 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: a94395023ff39e787f2fdc23dfe3fe4ccb57ff4c
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

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
 其行為取決於具名地區設定 `_Locname`。 每個建構函式都會以 [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`) 將其基底物件初始化。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




