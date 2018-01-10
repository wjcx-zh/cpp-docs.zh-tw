---
title: "PAINTSTRUCT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PAINTSTRUCT
dev_langs: C++
helpviewer_keywords: PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92583bba3dca60caa2895966a87571dc60805475
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT 結構
`PAINTSTRUCT`結構包含可以用來繪製視窗工作區的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagPAINTSTRUCT {  
    HDC hdc;  
    BOOL fErase;  
    RECT rcPaint;  
    BOOL fRestore;  
    BOOL fIncUpdate;  
    BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### <a name="parameters"></a>參數  
 *hdc*  
 識別要用來繪製的顯示內容。  
  
 *fErase*  
 指定是否需要重新繪製背景。 它不是 0，如果應用程式應重繪背景。 應用程式會負責繪製背景，如果 Windows 視窗類別建立不含背景筆刷 (請參閱描述**hbrBackground**隸屬[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構在 Windows SDK)。  
  
 *rcPaint*  
 指定的右上方，並降低要求在其中繪製的矩形的右角。  
  
 *fRestore*  
 保留的成員。 它是由 Windows 內部使用。  
  
 *fIncUpdate*  
 保留的成員。 它是由 Windows 內部使用。  
  
 *rgbReserved [16]*  
 保留的成員。 保留供內部使用 Windows 的記憶體區塊。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

