---
title: "Module::RegisterWinRTObject 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::RegisterWinRTObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegisterWinRTObject 方法"
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module::RegisterWinRTObject 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一或多個暫存器 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 讓其他應用程式可以連接至這些物件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>參數  
 `serverName`  
 指定此作業所影響的物件子集名稱。  
  
 `activatableClassIds`  
 註冊可啟動 Clsid 的陣列。  
  
 `cookie`  
 識別已註冊的類別物件的值。 若要撤銷註冊稍後會使用此值。  
  
 `count`  
 若要註冊的物件數目。  
  
## <a name="return-value"></a>傳回值  
 S_OK，如果登錄成功。否則，錯誤 HRESULT CO_E_OBJISREG 指出的原因，例如作業失敗。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [模組類別](../windows/module-class.md)