---
title: TN032：MFC 例外狀況機制
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: f3f13bb40151d3b9ef0d57c7e769ca30fa629177
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633386"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032：MFC 例外狀況機制

標準的 c + + 例外狀況機制，不支援舊版的 Visual c + + 和 MFC 提供巨集**TRY/CATCH/THROW**所使用。 此版本的 Visual C++ 完全支援 C++ 例外狀況。 此提示涵蓋先前巨集的一些進階實作詳細資料，包括如何自動清除堆疊式物件。 因為 C++ 例外狀況預設支援堆疊回溯，因此這個技術提示不再是必要的。

請參閱[例外狀況： 使用 MFC 巨集和 c + + 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)如需有關 MFC 巨集和新的 c + + 關鍵字之間的差異。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

