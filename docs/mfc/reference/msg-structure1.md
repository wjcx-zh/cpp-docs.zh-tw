---
title: MSG 結構 1 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41dbbcdd3404705a9ac7c6c7969a9ebeeb0238f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

