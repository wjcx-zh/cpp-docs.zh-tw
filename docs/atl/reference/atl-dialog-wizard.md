---
title: ATL 對話方塊精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e2d78f0a41edca44f8841d701cc87975c551466
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358002"
---
# <a name="atl-dialog-wizard"></a>ATL 對話方塊精靈
此精靈將插入至專案 ATL 對話方塊物件，衍生自[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 對話方塊衍生自`CAxDialogImpl`可以裝載 ActiveX 控制項。  
  
 精靈會建立預設的對話方塊資源**確定**和**取消**按鈕。 您可以編輯對話方塊資源，並加入 ActiveX 控制項使用[對話方塊編輯器](../../windows/dialog-editor.md)資源檢視中。  
  
 精靈將插入的標頭檔[訊息對應](../../atl/message-maps-atl.md)宣告處理預設的按一下事件。 請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)如需 ATL 對話方塊。  
  
 **簡短名稱**  
 設定 ATL 對話方塊物件的縮寫的名稱。 您提供的名稱判斷類別名稱和檔案 （.cpp 和.h） 名稱，除非您個別變更這些欄位。  
  
 `Class`  
 設定要建立之類別的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**，前面會加 'C'、 類別名稱的一般前置詞上。  
  
 **.h 檔案**  
 設定新的物件類別的標頭檔的名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存到您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選擇現有的檔案，精靈會無法將其儲存到選取的位置直到您按一下**完成**精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別宣告附加至檔案的內容。 按一下**是**附加檔案，按一下 **否**返回精靈並指定另一個檔案名稱。  
  
 **.cpp 檔案中**  
 設定新的物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存到您選擇的位置。 直到您按一下該檔案不儲存選取的位置**完成**精靈中。  
  
 精靈不會覆寫檔案。 如果當您按一下 選取現有的檔案名稱**完成**，精靈會提示您是否要在類別實作附加至檔案的內容。 按一下**是**附加檔案，按一下 **否**返回精靈並指定另一個檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 對話方塊](../../atl/reference/adding-an-atl-dialog-box.md)

