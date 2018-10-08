---
title: C 執行階段錯誤 R6008 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 604b54d1c1752c76e28680e3373913ca7e92a9bc
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860429"
---
# <a name="c-runtime-error-r6008"></a>C 執行階段錯誤 R6008

沒有足夠的空間，引數

> [!NOTE]
> 如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉因為它有內部記憶體問題。 有幾個可能的原因，這個錯誤，但通常極低的記憶體不足，太多記憶體，由環境變數或在程式中的 bug 所造成。
>
> 您可以嘗試進行下列步驟來修正這個錯誤：
>
> - 關閉其他正在執行的應用程式或重新啟動電腦以釋出記憶體。
> - 減少應用程式的數目和大小的命令列引數。
> - 使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> - 請檢查**Windows Update**中**控制台**軟體更新。
> - 檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

發生記憶體不足，無法載入程式，但沒有足夠的記憶體來建立**argv**陣列。 這可能造成極低的記憶體條件或非常大的命令列或環境變數的使用方式。 請考慮下列解決方案之一：

- 增加程式可以使用的記憶體的數量。

- 降低的數目和大小的命令列引數。

- 移除不必要的變數，以縮小環境大小。