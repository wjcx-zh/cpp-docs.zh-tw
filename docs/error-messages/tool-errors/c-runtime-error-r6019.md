---
title: C 執行階段錯誤 R6019 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95bc763ab39df16c1cfc1b05689560edecf70570
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093296"
---
# <a name="c-runtime-error-r6019"></a>C 執行階段錯誤 R6019

無法開啟主控台的裝置

> [!NOTE]
>  如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉，因為它嘗試存取主控台，但沒有足夠的權限。 有幾個可能的原因，這個錯誤，但通常是因為必須為系統管理員，以執行程式，或有一個錯誤是在程式中。
>
>  您可以嘗試進行下列步驟來修正這個錯誤：
>
>  -   系統管理員身分執行程式。
> -   使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> -   請檢查**Windows Update**中**控制台**軟體更新。
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

應用程式呼叫主控台函式，但作業系統未授與主控台的存取權，就會發生此錯誤。 除了在偵錯模式中，主控台函式通常不允許在 Microsoft Store 應用程式中。 如果您的應用程式需要系統管理員權限，才能執行，請確定它預設會安裝到系統管理員身分執行。