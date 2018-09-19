---
title: SAL 註釋 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __z annotation
- ref annotation
- _opt annotation
- __checkreturn annotatioin
- __deref_opt annotation
- deref_opt annotation
- __deref annotation
- __in annotation
- annotations [C++]
- z annotation
- _inout annotation
- __ref annotation
- full annotation
- _in annotation
- _ref annotation
- __out annotation
- _ecount annotation
- SAL annotations
- __opt annotation
- inout annotation
- in annotation
- _CA_SHOULD_CHECK_RETURN
- __bcount annotation
- _full annotation
- _bcount annotation
- deref annotation
- part annotation
- _out annotation
- __nz annotation
- __part annotation
- opt annotation
- __full annotation
- _nz annotation
- _z annotation
- out annotation
- __ecount annotation
- __inout annotation
- SAL annotations, _CA_SHOULD_CHECK_RETURN
- _deref_opt annotation
- _deref annotation
- nz annotation
- _part annotation
- ecount annotation
- bcount annotation
ms.assetid: 81893638-010c-41a0-9cb3-666fe360f3e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 363d7ff6de4c808c3c7b8d37a9a9f95bf069723c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107490"
---
# <a name="sal-annotations"></a>SAL 註釋

如果檢查程式庫標頭檔，您可能會注意到一些不尋常的註釋，例如 `_In_z` 和 `_Out_z_cap_(_Size)`。 這些是 Microsoft 原始程式碼註釋語言 (SAL) 的範例，它提供一組註釋說明函式如何使用它的參數，例如，其關於參數的假設和完成時的保證。 標頭檔 \<sal.h> 定義註釋。

如需在 Visual Studio 中使用 SAL 註釋的詳細資訊，請參閱[使用 SAL 註釋減少 C/C++ 程式碼缺失](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)。

## <a name="see-also"></a>請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)