---
title: "擷取函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbcd323292e301857c65d908047ab14948b86573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="extract-function"></a>擷取函式
**項目：**可讓您開啟的程式碼片段到它自己的函式。

**當：**某些需要從另一個函式呼叫的函式中有現有的程式碼片段。  

**原因：**您無法複製/貼上該程式碼，但這就可能會導致重複。  更好的解決方案是該片段重構與其他任何函式可以自由地呼叫它自己函數。

**如何：**

1. 反白顯示要擷取的程式碼：

   ![反白顯示的程式碼](images/extractfunction_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl + R**，然後**Ctrl + M**。  (請注意，根據您所選取的設定檔，鍵盤快速鍵可能會不同)。
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**擷取函式 （實驗）**從內容功能表。
   * **滑鼠**
     * 選取**編輯 > 重構 > 擷取函式 （實驗）**。
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**擷取函式 （實驗）**從內容功能表。
     * 按一下![Lightbulb](images/bulb.png)圖示出現在左邊的界，然後選取**擷取函式 （實驗）**從內容功能表。

1. 在**擷取函式/方法 （實驗）**視窗中，輸入新的函式名稱、 選取您想執行程式碼的放置，並按一下**確定** 按鈕。  

   ![擷取函式的函式](images/extractfunction_dialog.png)

1. 將建立新的函式在所指定，函式原型中對應的標頭檔，而原始的程式碼將會變更為呼叫該函式。

   ![擷取函式的結果](images/extractfunction_result.png)