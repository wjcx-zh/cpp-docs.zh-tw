---
title: 刪除開啟檔案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], deleting
ms.assetid: 4fba7fb2-df0a-458e-b760-8858e12b855c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8e66c811571f22c263193ffad676052b34b7f72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087093"
---
# <a name="deleting-open-files"></a>刪除開啟檔案

**ANSI 4.9.4.1**：移除函式在開啟檔案上會造成的影響

移除函式會刪除檔案。 如果檔案已開啟，則此函式會失敗且傳回 -1。

## <a name="see-also"></a>請參閱

[程式庫函式](../c-language/library-functions.md)