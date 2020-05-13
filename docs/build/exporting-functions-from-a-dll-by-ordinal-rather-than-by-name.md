---
title: 根據序數而不是名稱從 DLL 匯出函式
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328580"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>根據序數而不是名稱從 DLL 匯出函式

從 DLL 匯出函式的最簡單方式是依名稱匯出函式。 例如，當您使用 **__declspec （dllexport）** 時，就會發生這種情況。 但是您可以改為依序數匯出函式。 使用這項技術時，您必須使用 .def 檔案，而不是 **__declspec （dllexport）**。 若要指定函式的序數值，請將其序數附加至 .def 檔案中的函數名稱。 如需指定序數的詳細資訊，請參閱[使用 .def 檔案從 DLL 匯出](exporting-from-a-dll-using-def-files.md)。

> [!TIP]
> 如果您想要優化 DLL 的檔案大小，請在每個匯出的函數上使用**NONAME**屬性。 使用**NONAME**屬性時，序數會儲存在 DLL 的匯出資料表中，而不是函數名稱。 如果您要匯出許多函式，這可能會有相當大的節約。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [使用 .def 檔案，讓我可以依序數匯出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>請參閱

[從 DLL 匯出](exporting-from-a-dll.md)
