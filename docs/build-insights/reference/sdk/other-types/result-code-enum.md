---
title: RESULT_CODE 列舉
description: C++ BUILD Insights SDK RESULT_CODE 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ee563d148b3456b288bc418255ec46f8cbade7ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332296"
---
# <a name="result_code-enum"></a>RESULT_CODE 列舉

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`RESULT_CODE` 列舉會描述成功和失敗的狀況。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0（0x00000000） | 作業成功。 |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中的其中一個回呼函數會傳回 `CALLBACK_CODE_ANALYSIS_FAILURE` 值。 這個值是[CALLBACK_CODE](callback-code-enum.md)列舉的成員。 |
| `RESULT_CODE_FAILURE_CANCELLED` | 2（0x00000002） | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中的其中一個回呼函數會傳回 `CALLBACK_CODE_ANALYSIS_CANCEL` 值。 這個值是[CALLBACK_CODE](callback-code-enum.md)列舉的成員。 |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3（0x00000003） | 指定的 Windows 事件追蹤（ETW）追蹤無效。 |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4（0x00000004） | 指定的輸出 ETW 追蹤無效。 |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5（0x00000005） | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)結構未正確初始化。 |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6（0x00000006） | [RELOG_CALLBACKS](relog-callbacks-struct.md)結構未正確初始化。 |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7（0x00000007） | 無法開啟輸入 ETW 追蹤。 |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8（0x00000008） | 處理輸入 ETW 追蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9（0x00000009） | 嘗試啟動 relogging 會話時發生錯誤。 |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10（0x0000000A） | 輸入 ETW 追蹤遺漏重要的事件。 |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11（0x0000000B） | 您在不C++支援的 Windows 版本上使用 Build Insights。 |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12（0x0000000C） | 提供的會話名稱無效。 |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13（0x0000000D） | 此作業需要系統管理員許可權。 |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14（0x0000000E） | 產生 GUID 時發生錯誤。 |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15（0x0000000F） | 嘗試判斷臨時目錄路徑時發生錯誤。 |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16（0x00000010） | 嘗試建立要啟動之追蹤會話的臨時目錄時發生錯誤。 |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17（0x00000011） | 嘗試啟動系統追蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18（0x00000012） | 嘗試啟動 MSVC 追蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19（0x00000013） | 嘗試停止 MSVC 追蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20（0x00000014） | 嘗試啟動系統追蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21（0x00000015） | 追蹤已停止，但找不到追蹤會話的臨時目錄。 |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22（0x00000016） | 找不到正在停止之 MSVC 追蹤的追蹤檔案。 |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23（0x00000017） | 使用核心追蹤控制項合併追蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24（0x00000018） | 發生未知的錯誤。 |

::: moniker-end
