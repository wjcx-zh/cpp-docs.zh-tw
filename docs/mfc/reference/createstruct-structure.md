---
title: CREATESTRUCT 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e51aed1eb7f74c721a5a4da092f205a2492ba5f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370867"
---
# <a name="createstruct-structure"></a>CREATESTRUCT 結構
`CREATESTRUCT`結構會定義初始化參數傳遞至應用程式的視窗程序。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>參數  
 `lpCreateParams`  
 要用來建立視窗的資料點。  
  
 `hInstance`  
 識別擁有新的視窗中的模組的模組執行個體控制代碼。  
  
 `hMenu`  
 識別可供新的視窗功能表。 如果子視窗，包含整數識別碼。  
  
 `hwndParent`  
 識別擁有新視窗的視窗。 這個成員是**NULL**如果新的視窗是最上層視窗。  
  
 `cy`  
 指定新的視窗的高度。  
  
 `cx`  
 指定新的視窗的寬度。  
  
 `y`  
 指定新的視窗左上角的 y 座標。 如果新的視窗是子視窗; 座標是相對於父視窗否則座標是相對於螢幕原點。  
  
 `x`  
 指定新的視窗左上角的 x 座標。 如果新的視窗是子視窗; 座標是相對於父視窗否則座標是相對於螢幕原點。  
  
 `style`  
 指定新的視窗[樣式](../../mfc/reference/styles-used-by-mfc.md)。  
  
 `lpszName`  
 指向以 null 終止的字串，指定新的視窗名稱。  
  
 `lpszClass`  
 指向以 null 結束的字串，指定新視窗的視窗類別名稱 ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構; 如需詳細資訊，請參閱 Windows SDK)。  
  
 `dwExStyle`  
 指定[延伸樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)新視窗。  
  
## <a name="requirements"></a>需求  
 **標頭：** winuser.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


