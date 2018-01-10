---
title: "Event:: operator = 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de46ba0d6749120fc391b4a55527904ed1321ad9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventoperator-operator"></a>Event::operator= 運算子
將指定的 Event 參考指派給目前的 Event 執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 右值參考事件執行個體。  
  
## <a name="return-value"></a>傳回值  
 到目前的事件執行個體的指標。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [Event 類別 (Windows 執行階段 C++ 範本庫)](../windows/event-class-windows-runtime-cpp-template-library.md)