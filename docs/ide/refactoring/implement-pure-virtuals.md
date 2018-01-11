---
title: "實作純虛擬函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f311c2e5832754bfd785084b9aa930b5dbe43845
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implement-pure-virtuals"></a>實作純虛擬函式
**項目：**可讓您立即產生類別中實作所有純虛擬方法所需的程式碼。 

**當：**您想要繼承之類別的純虛擬函式。  

**原因：**不過這項功能會自動產生所有的方法簽章，您可以手動執行所有純虛擬函式的其中一個。

**如何：**

1. 文字或滑鼠將游標置於您要實作基底類別的純虛擬函式類別。

   ![反白顯示的程式碼](images/virtuals_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**實作所有純虛擬函式類別*ClassName*' * * 從內容功能表中，其中*ClassName*是所選類別的名稱。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**實作所有純虛擬函式類別*ClassName*' * * 從內容功能表中，其中*ClassName*是所選類別的名稱。

1. 純虛擬方法簽章將會自動建立，以便實作。

   ![實作純虛擬函式結果](images/virtuals_result.png)
