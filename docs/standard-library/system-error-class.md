---
title: "system_error 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "system_error/std::system_error"
  - "std.system_error"
  - "std::system_error"
  - "system_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "system_error 類別"
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# system_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代表所有報告低階系統錯誤擲回的例外狀況的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class system_error : public runtime_error {  
public:  
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,  
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

 };  
```  
  
## <a name="remarks"></a>備註  
 所傳回的值 `what` 類別中 [例外狀況](../standard-library/exception-class1.md) 建構從 `_Message` 和已儲存的物件型別的 [error_code](../standard-library/error-code-class.md) (可能是 `code` 或 `error_code(_Errval, _Errcat)`)。  
  
 成員函式 `code` 傳回儲存的 [error_code](../standard-library/error-code-class.md) 物件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< system_error >  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [\< system_error >](../standard-library/system-error.md)

