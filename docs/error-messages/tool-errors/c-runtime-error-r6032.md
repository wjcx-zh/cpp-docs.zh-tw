---
title: C 執行階段錯誤 R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: e0ae3acc491658840d74e262f3ab2719e613d60e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571336"
---
# <a name="c-runtime-error-r6032"></a>C 執行階段錯誤 R6032

沒有足夠的空間，如地區設定的詳細資訊

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉因為它有內部記憶體問題。 有幾個可能的原因，這個錯誤，但它通常會造成極低記憶體狀況，或在程式中的 bug。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式或重新啟動電腦以釋出記憶體。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

執行階段會維護上每個執行緒的地區設定的相關資訊，讓它可以處理皆區分地區設定函式的呼叫。 這項資訊的記憶體配置失敗，執行階段時無法繼續因為太多的基本功能，它依存於此。