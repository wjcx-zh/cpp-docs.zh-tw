---
title: 根據序數而不是名稱從 DLL 匯出函式
ms.date: 11/04/2016
f1_keywords:
- NONAME
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: fe34ec90aa775e7435d4a02b9d77a9cb9c8fdd65
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423296"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>根據序數而不是名稱從 DLL 匯出函式

從您的 DLL 匯出函式的最簡單方式是將它們匯出名稱。 這是當您使用時，會發生什麼事 **__declspec （dllexport)**，例如。 但是，您可以改為依序數匯出函式。 使用此技術，您必須使用.def 檔，而不是 **__declspec （dllexport)**。 若要指定函式的序數值，其序數在名稱後面附加函式.def 檔案中。 指定序數的相關資訊，請參閱[使用.def 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)。

> [!TIP]
>  如果您想要最佳化您的 DLL 檔案的大小，使用**NONAME**上每個匯出的函式的屬性。 具有**NONAME**屬性，序數會儲存在 DLL 的匯出資料表，而不是函式名稱。 如果您要匯出的許多功能，這可以是相當大的節省量。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用.def 檔，因此我可以依序數匯出](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>另請參閱

[從 DLL 匯出](../build/exporting-from-a-dll.md)
