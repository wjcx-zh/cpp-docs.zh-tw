---
title: "TerminateMap 函式 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::TerminateMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TerminateMap 函式"
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TerminateMap 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 結構，而且不能直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>參數  
 `module`  
 A [模組](../windows/module-class.md)。  
  
 `serverName`  
 參數所指定的模組中的 class factory 的子集名稱 `module`。  
  
 `forceTerminate`  
 `true` 終止類別處理站，不論它們是作用中。 `false` 不終止 class factory，如果任何 factory 作用中。  
  
## <a name="return-value"></a>傳回值  
 `true` 如果已經結束所有的 class factory。否則， `false`。  
  
## <a name="remarks"></a>備註  
 關閉指定的模組中的類別處理站。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間︰** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)