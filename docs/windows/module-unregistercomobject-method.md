---
title: "Module::UnregisterCOMObject 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Module::UnregisterCOMObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UnregisterCOMObject 方法"
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::UnregisterCOMObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取消登錄一或多個 COM 物件，防止其他應用程式連接到它們。  
  
## <a name="syntax"></a>語法  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
#### <a name="parameters"></a>參數  
 `serverName`  
 （未使用）  
  
 `cookies`  
 識別要移除註冊的類別物件的值的指標陣列。 陣列由 [RegisterCOMObject](../windows/module-registercomobject-method.md) 方法。  
  
 `count`  
 若要取消註冊的類別數目。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果此作業成功。否則，錯誤 HRESULT，表示原因的作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)