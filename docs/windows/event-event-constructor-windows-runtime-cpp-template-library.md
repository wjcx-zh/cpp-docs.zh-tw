---
title: "Event:: event 建構函式 （Windows 執行階段 c + + 樣板程式庫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs: C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88fafd4bb345d8e70f84aa87c04592e91703b5c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event 建構函式 (Windows 執行階段 C++ 樣板程式庫)
初始化 Event 類別的新執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 事件的控制代碼。 根據預設，`h` 初始化為 `nullptr`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Event 類別 (Windows 執行階段 C++ 範本庫)](../windows/event-class-windows-runtime-cpp-template-library.md)