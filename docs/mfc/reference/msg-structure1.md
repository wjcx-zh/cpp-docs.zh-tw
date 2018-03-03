---
title: "MSG 結構 1 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b504f116dcbff7fa45e741ff9715070ee0c74583
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="msg-structure1"></a>MSG 結構 1
`MSG`結構包含從執行緒訊息佇列的訊息資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagMSG {     // msg    
    HWND hwnd;  
    UINT message;  
    WPARAM wParam;  
    LPARAM lParam;  
    DWORD time;  
    POINT pt;  
} MSG;  
```  
  
#### <a name="parameters"></a>參數  
 *hwnd*  
 識別的視窗的視窗程序接收的訊息。  
  
 `message`  
 指定的訊息編號。  
  
 `wParam`  
 指定訊息的其他資訊。 確切意義取決於值**訊息**成員。  
  
 `lParam`  
 指定訊息的其他資訊。 確切意義取決於值**訊息**成員。  
  
 `time`  
 指定公佈訊息的時間。  
  
 `pt`  
 公佈訊息時，請指定資料指標位置，以螢幕座標。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

