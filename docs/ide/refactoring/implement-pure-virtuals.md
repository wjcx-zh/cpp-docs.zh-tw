---
title: 實作純虛擬函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 234ae9a67bcbc60ea156fbacb5169d0bd1573a91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442756"
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
