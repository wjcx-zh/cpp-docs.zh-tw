---
title: 實作純虛擬函式 |Microsoft 文件
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
ms.openlocfilehash: afce516f2718a76658846ed4f992aeabff75330b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implement-pure-virtuals"></a>實作純虛擬函式
**項目：**可讓您立即產生類別中實作所有純虛擬方法所需的程式碼。 

**當：**您想要繼承之類別的純虛擬函式。  

**原因：**不過這項功能會自動產生所有的方法簽章，您可以手動執行所有純虛擬函式的其中一個。

**做法：**

1. 文字或滑鼠將游標置於您要實作基底類別的純虛擬函式類別。

   ![醒目標示的程式碼](images/virtuals_highlight.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 觸發程序**快速控制項目及重構**功能表，然後選取**實作所有純虛擬函式類別*ClassName*'** 從內容功能表中，其中*ClassName*是所選類別的名稱。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**實作所有純虛擬函式類別*ClassName*'** 從內容功能表中，其中*ClassName*是所選類別的名稱。

1. 純虛擬方法簽章將會自動建立，以便實作。

   ![實作純虛擬函式結果](images/virtuals_result.png)
