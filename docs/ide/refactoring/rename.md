---
title: "重新命名 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ca06ef5a11d674d35aff7276e14312c456c60e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rename"></a>重新命名
**項目：**可讓您重新命名程式碼的符號，例如欄位、 區域變數、 方法、 命名空間、 屬性和類型的識別項。

**當：**您想要安全地重新命名的項目，而不必尋找所有執行個體，並複製/貼上的新名稱。  

**原因：**複製並貼上整個專案的新名稱可能會導致錯誤。  這項重構工具正確地將執行重新命名動作。

**如何：**

1. 反白顯示，或將文字指標放置在重新命名項目：

   ![反白顯示的程式碼](images/rename_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + R**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
   * **滑鼠**
     * 選取**編輯 > 重構 > 重新命名**。
     * 以滑鼠右鍵按一下程式碼，然後選取**重新命名**。

1. 在**重新命名**視窗快顯出現，輸入新名稱的選取的項目，然後按一下**預覽** 按鈕。  變更**搜尋範圍**如果您要放大或縮小重新命名的範圍。

   ![重新命名對話方塊](images/rename_dialog.png)

   > [!TIP]
   > 您可以藉由檢查略過預覽**略過預覽變更，如果所有確認參考**選項。

1. 當**預覽變更-重新命名**視窗隨即出現，請確認您所要求的變更已適當地進行。  使用中視窗的上半部的核取方塊，啟用或停用的任何項目重新命名。

   ![重新命名預覽](images/rename_preview.png)

1. 當一切良好時，按一下 **套用**按鈕與項目將會重新命名您的原始程式碼中。
