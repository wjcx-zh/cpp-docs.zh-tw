---
title: DHtmlUrlEventMapEntry 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee629d9dcffc80ce20306989cad72d466722af87
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123327"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry 結構
`DHtmlUrlEventMapEntry`結構提供多個 URL 事件對應支援。  
  
## <a name="syntax"></a>語法  
  
```  
struct DHtmlUrlEventMapEntry  
{  
LPCTSTR szUrl;  
const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### <a name="parameters"></a>參數  
 *szUrl*  
 URL。  
  
 *pEventMap*  
 事件對應 URL 與相關聯。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdhtml.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

