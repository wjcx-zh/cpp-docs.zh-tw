---
title: C 執行階段錯誤 R6026 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6026
dev_langs:
- C++
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b10075912ce4fde65699cf7b2d413c0bdd10f0
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860793"
---
# <a name="c-runtime-error-r6026"></a>C 執行階段錯誤 R6026

沒有足夠的空間 stdio 初始化

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉因為它有內部記憶體問題。 有幾個可能的原因，這個錯誤，但通常極低的記憶體不足所引起。 此外，它也可能造成應用程式中的錯誤、 損毀，它會使用時，Visual c + + 程式庫或驅動程式。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式或重新啟動電腦以釋出記憶體。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 如果應用程式所使用的另一個應用程式或驅動程式安裝之前，使用**應用程式和功能**或是**程式和功能**頁面**控制台**移除新的應用程式或驅動程式，然後重試您的應用程式。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝 Microsoft Visual c + + 可轉散發套件的所有複本。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

當沒有足夠的記憶體可用來初始化標準 I/O 支援在 C 執行階段時，就會發生此錯誤。 在應用程式啟動時通常會發生此錯誤。 請確認，您的應用程式的驅動程式和其所載入的 dll 執行不會損毀在啟動堆積。