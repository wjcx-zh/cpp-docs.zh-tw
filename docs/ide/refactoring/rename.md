---
title: 重新命名 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a064527f6afcbf91be3fb4e51180be647c1f506
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339809"
---
# <a name="rename"></a>重新命名
**功能：** 讓您重新命名程式碼符號 (例如欄位、區域變數、方法、命名空間、屬性及類型) 的識別碼。

**時機：** 您想要安全地重新命名某個項目，而無須尋找所有執行個體及複製/貼上新名稱。  

**原因：** 在整個專案複製並貼上新名稱可能造成錯誤。  這個重構工具將可正確地執行重新命名動作。

**做法：**

1. 醒目標示要重新命名的項目，或將文字游標放在要重新命名的項目內：

   ![醒目標示的程式碼](images/rename_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **CTRL+R**，再按 **CTRL+R**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
   * **滑鼠**
     * 選取 [編輯] > [重構] > [重新命名]。
     * 在程式碼上按一下滑鼠右鍵，然後選取 [重新命名]。

1. 在顯示的 [重新命名] 視窗中，輸入所選項目的新名稱，然後按一下 [預覽] 按鈕。  如果您需要放大或縮小重新命名的範圍，請變更 [搜尋範圍]。

   ![[重新命名] 對話方塊](images/rename_dialog.png)

   > [!TIP]
   > 您可以核取 [如果確認所有參考，則略過預覽變更] 選項來略過預覽。

1. 當 [預覽變更 - 重新命名] 視窗出現時，確定您所要求的變更已適當地進行。  使用視窗上半部的核取方塊，啟用或停用任何項目的重新命名。

   ![重新命名預覽](images/rename_preview.png)

1. 如果看起來沒問題，請按一下 [套用] 按鈕，即會重新命名您原始程式碼中的項目。
