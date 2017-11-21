---
title: "Handlet:: Close 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs: C++
helpviewer_keywords: Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 94c246153e5c7e159ccbfe4196ab3692f4138047
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="handletclose-method"></a>HandleT::Close 方法
關閉目前的 HandleT 物件。  
  
## <a name="syntax"></a>語法  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>備註  
 做為目前 HandleT 的控制代碼會關閉，而 HandleT 設為無效的狀態。  
  
 如果控制代碼不正確地關閉，會呼叫的執行緒中引發例外狀況。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)