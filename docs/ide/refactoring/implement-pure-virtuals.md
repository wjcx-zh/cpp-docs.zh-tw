---
title: 實作純虛擬函式
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: 59e4519f57a1d9bd9ba1cee1ed6ae41bea785a9f
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692657"
---
# <a name="implement-pure-virtuals"></a>實作純虛擬函式

**功能：** 讓您立即產生在類別中實作所有純虛擬方法所需的程式碼。

**時機：** 您想要繼承自具有純虛擬函式的類別。

**原因：** 您可以手動逐一實作所有純虛擬函式；不過，此功能將可自動產生所有方法簽章。

**做法：**

1. 將文字或滑鼠游標置於您要實作基底類別之純虛擬函式的類別。

   ![醒目標示的程式碼](images/virtuals_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 觸發 [快速動作及重構] 功能表，然後從操作功能表選取 [實作類別 '*ClassName*' 的所有純虛擬函式]，其中 *ClassName* 是所選類別的名稱。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表，然後從操作功能表選取 [實作類別 '*ClassName*' 的所有純虛擬函式]，其中 *ClassName* 是所選類別的名稱。

1. 系統將會自動建立純虛擬方法簽章，並備妥以供實作。

   ![實作純虛擬函式結果](images/virtuals_result.png)
