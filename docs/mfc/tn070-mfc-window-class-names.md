---
title: 'TN070: MFC 視窗類別名稱 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.classes
dev_langs:
- C++
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c66c434503bbd2c6d7ee1b0557fa73d843e0caaa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tn070-mfc-window-class-names"></a>TN070：MFC 視窗類別名稱
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 MFC 視窗會使用動態建立的類別名稱反映視窗的功能。 MFC 會動態為應用程式所產生的框架視窗、檢視和快顯視窗，產生類別名稱。 不確定視窗的類別時，MFC 應用程式所產生的對話方塊和控制項會使用 Windows 所提供的名稱。  
  
 您可以取代動態提供的類別名稱註冊您自己的視窗類別和使用中的覆寫[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)。 MFC 提供的類別名稱採用下列兩種格式之一：  
  
```  
Afx:%x:%x  
Afx:%x:%x:%x:%x:%x  
```  
  
 十六進位數字取代`%x`字元會從資料填入[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)結構。 MFC 使用這項技術，讓多個需要相同的 c + + 類別**WNDCLASS**結構可以共用相同的已註冊的視窗類別。 不同於大部分簡易的 Win32 應用程式，MFC 應用程式只能有一個**WNDPROC**，因此您可以輕鬆地共用**WNDCLASS**結構，以節省時間和記憶體。 可取代以上所顯示 `%x` 字元的值如下：  
  
- **WNDCLASS.hInstance**  
  
- **WNDCLASS.style**  
  
- **WNDCLASS.hCursor**  
  
- **WNDCLASS.hbrBackground**  
  
- **WNDCLASS.hIcon**  
  
 第一種形式 (`Afx:%x:%x`) 時會使用**hCursor**， **hbrBackground**，和**hIcon**全部**NULL**。  
  
## <a name="see-also"></a>另請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)   
 [TN020：識別碼命名和編號慣例](../mfc/tn020-id-naming-and-numbering-conventions.md)

