---
title: "自訂建置步驟屬性 (Linux C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: ae749fa161dba2957f3e621ce42c610153594e66
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="custom-build-step-properties-linux-c"></a>自訂建置步驟屬性 (Linux C++)

屬性 | 描述
--- | ---
命令列 | 會由自訂建置步驟執行的命令。
描述 | 當自訂建置步驟執行時所顯示的訊息。
輸出 | 自訂建置步驟所產生的輸出檔。 必須要有這項設定，累加建置才能正常運作。
其他相依性 | 用於自訂建置步驟之任何其他輸入檔以分號分隔的清單。
後執行與先執行 | 這些選項定義自訂建置步驟在建置流程中執行的時間點 (相對於所列出的目標)。 最常列出的目標是 BuildGenerateSources、BuildCompile 和 BuildLink，因為這些目標代表建置流程中的主要步驟。 其他常列目標包括 Midl、CLCompile 和 Link。
將輸出視為內容 | 此選項在 Windows 市集或 Windows Phone 應用程式中才有用處，其所有內容檔都包含在 .appx 套件中。