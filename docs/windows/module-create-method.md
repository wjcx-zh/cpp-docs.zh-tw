---
title: "Module::Create 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::Create"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Create 方法"
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::Create 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立模組的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW static Module& Create();  
template<  
   typename T  
>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<  
   typename T  
>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 模組類型。  
  
 `callback`  
 釋放最後一個執行個體物件的模組時呼叫。  
  
 `object`  
  `object` 和 `method` 參數搭配使用的。 點的最後一個執行個體物件時釋放最後一個執行個體物件模組中。  
  
 `method`  
  `object` 和 `method` 參數搭配使用的。 當使用者放開最後一個執行個體物件模組中的最後一個執行個體物件的方法指標。  
  
## <a name="return-value"></a>傳回值  
 模組參考。  
  
## <a name="requirements"></a>需求  
 **標頭︰** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
[模組類別](../windows/module-class.md)

 