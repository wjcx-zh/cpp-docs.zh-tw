---
title: 嚴重錯誤 C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 5ab98c46d60d15cdcb6de22aa922d62453d41880
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204486"
---
# <a name="fatal-error-c1047"></a>嚴重錯誤 C1047

物件或程式庫檔案 'file' 是使用比其他物件更舊的編譯器建立的，請重建舊物件和程式庫

如果由 **/LTCG** 所建置的目的檔或程式庫連結在一起，但這些目的檔或程式庫是使用不同版本的 Visual C++ 工具組所建置，則會造成 C1047。

如果您開始使用新版本的編譯器，但不會執行現有目的檔或程式庫的全新重建，則可能會發生這種情況。

若要解決 C1047，請重建所有目的檔或程式庫。
