---
title: "PAINTSTRUCT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 07b79b9ae20bd6e5648c67fa277ddde2929028c7
ms.lasthandoff: 02/24/2017

---
# <a name="paintstruct-structure"></a>PAINTSTRUCT 結構
`PAINTSTRUCT`結構包含可以用來繪製的視窗工作區的資訊。  
  
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
 指定是否需要重新繪製背景。 它不是 0，如果應用程式應該重繪背景。 應用程式會負責繪製背景，如果 Windows 視窗類別建立時沒有背景筆刷 (請參閱說明**hbrBackground**成員[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)])。  
  
 *rcPaint*  
 指定的右上方，而要求在其中繪製的矩形的右角。  
  
 *fRestore*  
 保留的成員。 它是由 Windows 內部使用。  
  
 *fIncUpdate*  
 保留的成員。 它是由 Windows 內部使用。  
  
 *rgbReserved [16]*  
 保留的成員。 保留的內部 Windows 所使用的記憶體區塊。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)


