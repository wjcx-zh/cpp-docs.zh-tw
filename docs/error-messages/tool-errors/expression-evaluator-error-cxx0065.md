---
title: 運算式評估工具錯誤 CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299312"
---
# <a name="expression-evaluator-error-cxx0065"></a>運算式評估工具錯誤 CXX0065

變數必須有堆疊框架

運算式包含變數存在於目前的範圍內，但尚未尚未建立。

當您已逐步函式，但尚未設定的函式之堆疊框架的初構，或如果您已逐步函式的結束代碼，就會發生此錯誤。

之前已設定的堆疊框架評估運算式之前，請逐步初構程式碼。

此錯誤是與 can0065 相同。