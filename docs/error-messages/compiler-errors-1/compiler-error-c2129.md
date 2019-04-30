---
title: 編譯器錯誤 C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397623"
---
# <a name="compiler-error-c2129"></a>編譯器錯誤 C2129

靜態函式 'function' 宣告但未定義

向前參考對`static`永遠不會定義函式。

A`static`函式必須在檔案範圍內定義。 如果函式定義於另一個檔案，它必須宣告`extern`。