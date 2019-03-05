---
title: ATL 對話方塊精靈
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 043c170021ce1ceb072dba3e5a450375f556753a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287917"
---
# <a name="atl-dialog-wizard"></a>ATL 對話方塊精靈

此精靈會插入到專案 ATL 對話方塊物件，衍生自[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)。 對話方塊中衍生自`CAxDialogImpl`可以裝載 ActiveX 控制項。

精靈會建立對話方塊資源，預設值 **[確定]** 並**取消**按鈕。 您可以編輯對話方塊資源，並加入 ActiveX 控制項使用[對話方塊編輯器](../../windows/dialog-editor.md)資源檢視中。

當精靈插入標頭檔[訊息對應](../../atl/message-maps-atl.md)宣告處理預設的按一下事件。 請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)的 ATL 對話方塊的詳細資訊。

- **簡短名稱**

   設定 ATL 對話方塊物件的縮寫的名稱。 您提供的名稱會決定類別名稱和檔案 （.cpp 和.h） 名稱，除非您個別變更這些欄位。

- **類別**

   設定要建立之類別的名稱。 這個名稱根據您在中提供的名稱**簡短名稱**前面 'C'，類別名稱的一般前置詞加上。

- **.h 檔案**

   設定新物件類別的標頭檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置，或將類別宣告附加至現有的檔案。 如果您選擇現有的檔案，在您按一下精靈中的 [完成] 之前，精靈不會將它儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別宣告附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

- **.cpp 檔案**

   設定新物件類別的實作檔名稱。 根據預設，這個名稱根據您在中提供的名稱**簡短名稱**。 按一下省略符號按鈕，將檔案名稱儲存至您選擇的位置。 在您按一下精靈中的 [完成] 之前，檔案不會儲存至選取的位置。

   精靈不會覆寫檔案。 如果您選取現有檔案的名稱，當您按一下 [完成] 時，精靈會提示您指出是否應該將類別實作附加至檔案的內容。 按一下 [是] 可附加檔案，按一下 [否] 可返回精靈並指定另一個檔案名稱。

## <a name="see-also"></a>另請參閱

[ATL 對話方塊](../../atl/reference/adding-an-atl-dialog-box.md)
