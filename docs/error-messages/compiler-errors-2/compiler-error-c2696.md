---
title: 編譯器錯誤 C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367599"
---
# <a name="compiler-error-c2696"></a>編譯器錯誤 C2696

無法建立受管理的類型 'type' 的暫存物件

若要參考`const`在未受管理的程式會導致編譯器呼叫建構函式，並在堆疊上建立暫存物件。 不過，managed 的類別永遠不會在堆疊上建立。

C2696 才可使用過時的編譯器選項 **/clr: oldsyntax**。
