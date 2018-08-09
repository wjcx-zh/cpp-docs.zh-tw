---
title: 'Handlet:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7cbe76cdea5c8fadef818ede1d63d88e4437bdae
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651063"
---
# <a name="handletclose-method"></a>HandleT::Close 方法
關閉目前**HandleT**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void Close();  
```  
  
## <a name="remarks"></a>備註  
 控制代碼就是目前的基礎**HandleT**已關閉，而**HandleT**設為無效的狀態。  
  
 如果控制代碼不正確關閉，就會呼叫的執行緒中引發例外狀況。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HandleT 類別](../windows/handlet-class.md)