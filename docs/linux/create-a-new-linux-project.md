---
title: "建立新的 Linux 專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: e0a92f82413702c639af4a2cd4c4cc62abcce2b2
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---

# <a name="create-a-new-linux-project"></a>建立新的 Linux 專案

若要在 Visual Studio 中建立新的 Linux 專案，請執行下列動作：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]，或按 **Ctrl+Shift+N**。
1. 選取 [範本] > [其他語言] > [Visual C++] > [跨平台] > [Linux] 節點，然後選取您要建立的專案類型、輸入「名稱/位置」並按一下 [確定]。

   ![新的 Linux 專案](media/newproject.png)

   | 專案類型 | 描述
   | ------------ | ---
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，並撰寫範例程式碼讓 LED 閃爍
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，並撰寫範例程式碼以將文字輸出至主控台
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，但未撰寫任何範例程式碼
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 建置系統所建置之 Linux 電腦為目標的專案


