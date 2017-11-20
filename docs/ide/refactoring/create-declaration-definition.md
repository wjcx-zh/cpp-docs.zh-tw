---
title: "建立宣告 / 定義 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25f622cbd71195e75907b113e12e4d40ef0ec912
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="create-declaration--definition"></a>建立宣告/定義
**項目：**可讓您立即產生的宣告或定義函式。

**當：**有函式需要 delcaration，反之亦然。  

**原因：**您可以手動建立宣告/定義，但這會自動建立，視需要建立標頭/程式碼檔案。

**如何：**

1. 文字或滑鼠將游標置於您要建立宣告或定義的函數。

   ![反白顯示的程式碼](images/createdefinition_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**建立宣告 / 定義**從內容功能表。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**建立宣告 / 定義**從內容功能表。

1. 在來源或標頭檔中，您會看到快顯預覽視窗中，將會建立函式的宣告/定義。  如果來源或標頭檔不存在，它也會是建立並放在專案中。

   ![建立宣告 / 定義產生](images/createdefinition_result.png)
