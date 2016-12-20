---
title: "ComPtr::As 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::As"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "As 方法"
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::As 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回 ComPtr 物件，代表指定範本參數所識別的介面。  
  
## <a name="syntax"></a>語法  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>參數  
 `U`  
 參數所表示的介面 `p`。  
  
 `p`  
 ComPtr 物件，表示參數所指定的介面 `U`。 參數 `p` 不可參考目前 ComPtr 物件。  
  
## <a name="remarks"></a>備註  
 第一個範本是程式碼中應該使用的表單。 第二個範本是內部的協助程式特製化支援 c + + 語言功能，例如 [自動](../cpp/auto-cpp.md) 類型推算關鍵字。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [ComPtr 類別](../windows/comptr-class.md)