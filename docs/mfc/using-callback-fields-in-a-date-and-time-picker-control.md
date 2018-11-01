---
title: 在日期時間選擇器控制項中使用回呼欄位
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 82dd4bac53b419b531f512aff859510d6603d462
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564238"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>在日期時間選擇器控制項中使用回呼欄位

除了定義日期和時間選擇器欄位的標準格式字元以外，您也可以將自訂格式字串的某些部分指定為回呼欄位，以自訂輸出。 若要宣告回呼欄位，請在格式字串主體的任何位置包含一個或多個 "X" 字元 (ASCII 碼 88)。 例如，下列字串 "Today is: 'yy'/'MM'/'dd' (Day 'X')" 可讓日期和時間選擇器控制項以年、月、日、年的天數來顯示目前的值。

> [!NOTE]
>  回呼欄位的 X 數目不會對應至要顯示的字元數目。

您可以重複 "X" 字元，以區別自訂字串的多個回呼欄位。 因此，格式字串 "XXddddMMMdd', 'yyyXXX" 包含兩個唯一的回呼欄位 "XX" 和 "XXX"。

> [!NOTE]
>  回呼欄位視為有效的欄位，因此您的應用程式必須準備好處理 DTN_WMKEYDOWN 通知訊息。

實作日期和時間選擇器控制項的回呼欄位，包含三個部分：

- 初始化自訂格式字串

- 處理 DTN_FORMATQUERY 通知

- 處理 DTN_FORMAT 通知

## <a name="initializing-the-custom-format-string"></a>初始化自訂格式字串

呼叫 `CDateTimeCtrl::SetFormat` 以初始化自訂字串。 如需詳細資訊，請參閱 <<c0> [ 日期和時間選擇器控制項中使用自訂格式字串](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)。 設定自訂格式字串的位置通常是在包含對話方塊類別的 `OnInitDialog` 函式，或是包含檢視類別的 `OnInitialUpdate` 函式中。

## <a name="handling-the-dtnformatquery-notification"></a>處理 DTN_FORMATQUERY 通知

當控制項剖析格式字串並遇到回呼欄位時，應用程式會傳送 DTN_FORMAT 和 DTN_FORMATQUERY 通知訊息。 回呼欄位字串包含通知，讓您可以判斷哪一個回呼欄位正在進行查詢。

DTN_FORMATQUERY 通知會傳送至擷取像素為單位，在字串中會顯示在目前回呼欄位的允許大小上限。

若要適當地計算這個值，您必須使用控制項的顯示字型，計算要替代之欄位的字串高度和寬度。 藉由呼叫，輕鬆實現字串的實際計算[GetTextExtentPoint32](/windows/desktop/api/wingdi/nf-wingdi-gettextextentpoint32a) Win32 函式。 一旦決定大小後，請將值傳遞至應用程式並結束處理函式。

下列範例是一種提供回呼字串大小的方法：

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

計算目前回呼欄位的大小後，您必須為該欄位提供值。 這是 DTN_FORMAT 通知的處理常式。

## <a name="handling-the-dtnformat-notification"></a>處理 DTN_FORMAT 通知

應用程式使用 DTN_FORMAT 通知，要求將被取代的字元字串。 下列範例說明其中一種方法：

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  將指標**NMDATETIMEFORMAT**找到結構轉型為正確的類型的通知處理常式的第一個參數。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

