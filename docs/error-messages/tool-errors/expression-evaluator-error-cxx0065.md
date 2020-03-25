---
title: 運算式評估工具錯誤 CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184420"
---
# <a name="expression-evaluator-error-cxx0065"></a>運算式評估工具錯誤 CXX0065

變數需要堆疊框架

運算式包含的變數存在於目前的範圍內，但尚未建立。

當您逐步執行函式的初構，但尚未設定函式的堆疊框架，或如果您已逐步執行函式的結束代碼時，就會發生這個錯誤。

逐步執行初構程式碼，直到在評估運算式之前設定堆疊框架為止。

此錯誤與 CAN0065 相同。
