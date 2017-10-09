---
title: "UICheckState 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- afxwinforms/uicheckstate
dev_langs:
- C++
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 21b23efdbad9f2b867b104d0a0d9d0bbb4338e5a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---

# <a name="uicheckstate-enumeration"></a>UICheckState 列舉
描述命令的使用者介面項目核取狀態。  
   
### <a name="syntax"></a>語法   
```  
public enum class 
{  
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]  
   Unchecked,   
   Checked,   
   Indeterminate 
};  
```  
   
### <a name="remarks"></a>備註  
 [ICommandUI::Check](icommandui-interface.md#check)會使用這些值來描述使用者介面項目的狀態。    
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  

