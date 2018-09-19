---
title: C 執行階段錯誤 R6031 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6031
dev_langs:
- C++
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83dbcdc433ea731e6ddf0765b4b3a55d5707f429
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059494"
---
# <a name="c-runtime-error-r6031"></a>C 執行階段錯誤 R6031

嘗試多次初始化 CRT。 這表示您的應用程式中的 bug。

> [!NOTE]
>  如果您遇到這個錯誤訊息時執行應用程式時，應用程式已關閉發生內部問題。 原因可能是 bug 在應用程式，或附加元件或應用程式使用的擴充功能中的 bug。
>
>  您可以嘗試進行下列步驟來修正這個錯誤：
>
>  -   使用**應用程式和功能**或是**程式和功能**頁面**控制台**修復或重新安裝程式。
> -   使用**應用程式和功能**或是**程式和功能**頁面**控制台**移除，請修復或重新安裝應用程式使用任何附加元件或擴充程式。
> -   請檢查**Windows Update**中**控制台**軟體更新。
> -   檢查應用程式的更新版本。 如果問題持續發生，請連絡應用程式廠商。

**適用於程式設計人員的資訊**

這項診斷表示 MSIL 指示在執行期間載入器鎖定。 如需詳細資訊，請參閱 <<c0> [ 初始化混合組件](../../dotnet/initialization-of-mixed-assemblies.md)。