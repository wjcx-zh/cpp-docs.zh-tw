---
title: 編譯器警告 (層級 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: c1de07cd65bbc9f02a979ceebe31be4143af70ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175814"
---
# <a name="compiler-warning-level-1-c4276"></a>編譯器警告 (層級 1) C4276

' function '：未提供原型;假設沒有任何參數

當您以[__stdcall](../../cpp/stdcall.md)呼叫慣例取得函式的位址時，您必須提供原型，讓編譯器能夠建立函式的裝飾名稱。 由於*函式沒有原型*，因此，編譯器在建立裝飾名稱時，會假設函式沒有任何參數。
