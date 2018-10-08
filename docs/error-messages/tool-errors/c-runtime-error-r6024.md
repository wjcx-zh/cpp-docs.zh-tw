---
title: C 執行階段錯誤 R6024 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6024
dev_langs:
- C++
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df874ae68f786585e85a8bc1b01ea8d0ac831d87
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861287"
---
# <a name="c-runtime-error-r6024"></a>C 執行階段錯誤 R6024

_onexit/atexit 資料表空間不足

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉因為它有內部記憶體問題。 此錯誤通常是在極低記憶體狀況，很少程式中的 bug 或它所使用的 Visual c + + 程式庫的損毀所致。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式或重新啟動電腦以釋出記憶體。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝 Microsoft Visual c + + 可轉散發套件的所有複本。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

會發生這個錯誤，因為沒有任何記憶體可供`_onexit`或`atexit`函式。 此錯誤被因為記憶體不足的狀況。 您可以考慮在記憶體不足狀況的預先配置的緩衝區，可協助將使用者資料儲存及執行全新的應用程式的應用程式啟動時結束。