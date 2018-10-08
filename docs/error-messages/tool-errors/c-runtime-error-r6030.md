---
title: C 執行階段錯誤 R6030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d25969a9ecb833c53b93135e65fa27b4f005a0d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861196"
---
# <a name="c-runtime-error-r6030"></a>C 執行階段錯誤 R6030

未初始化的 CRT

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉發生內部問題。 此問題通常是在特定安全性軟體程式，或很少，在程式中的錯誤所導致。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 您的安全性軟體可能會有特定的指示來解決此問題。 檢查安全性軟體廠商的網站，如需詳細資訊。 或者，請檢查您的安全性軟體的更新版本，或嘗試不同的安全性軟體。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

如果您使用 C 執行階段 (CRT)，但未執行 CRT 啟始程式碼，就會發生此錯誤。 它是可能發生這個錯誤，如果連結器切換[/ENTRY](../../build/reference/entry-entry-point-symbol.md)用來覆寫預設的起始位址，通常**mainCRTStartup**， **wmainCRTStartup**的主控台 EXE **WinMainCRTStartup**或是**wWinMainCRTStartup** Windows exe，或 **_DllMainCRTStartup** dll。 除非在啟動時要呼叫的其中一個上述函數，將不會初始化 C 執行階段。 啟動呼叫這些函數通常根據預設，當您連結到 C 執行階段程式庫，並使用一般**主要**， **wmain**， **WinMain**，或**DllMain**進入點。

它也是可能發生這個錯誤，當其他程式使用程式碼資料隱碼攻擊技巧來攔截特定的 DLL 程式庫呼叫。 某些具侵入性的安全性程式會使用這項技術。 在 Visual Studio 2015 之前的 Visual c + + 版本中，就可以使用以靜態方式連結的 CRT 程式庫來解決問題，但這不建議用於安全性和應用程式更新的原因。 修正此問題，可能需要使用者動作。