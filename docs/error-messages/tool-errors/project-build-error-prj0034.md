---
title: 專案建置錯誤 PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: 7c078a3d2aef24df9151cb10f81c1b7423809e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347583"
---
# <a name="project-build-error-prj0034"></a>專案建置錯誤 PRJ0034

'其他相依性' 屬性，專案層級自訂建置步驟包含 'macro' 它評估成 'macro_expansion'。

在專案上的自訂建置步驟包含它可能是因為巨集評估問題的其他相依性中的錯誤。 這項錯誤也可能表示，格式不正確的路徑，是包含字元或在檔案路徑中不合法的字元的組合。

若要解決這個錯誤，修正巨集或修正的路徑規格。 評估的路徑是從專案目錄的絕對路徑。