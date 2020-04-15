---
title: RESULT_CODE枚舉
description: C++生成見解 SDK RESULT_CODE枚舉引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62874e176c3f3e8f9df1ca64e7b593b7a0ef5c01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323627"
---
# <a name="result_code-enum"></a>RESULT_CODE枚舉

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`RESULT_CODE`舉描述了成功和失敗的情況。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x000000) | 作業成功。 |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中的回調函數之`CALLBACK_CODE_ANALYSIS_FAILURE`一返回該 值。 此值是[CALLBACK_CODE](callback-code-enum.md)枚舉的成員。 |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x0000002) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)或[RELOG_DESCRIPTOR](relog-descriptor-struct.md)中的回調函數之`CALLBACK_CODE_ANALYSIS_CANCEL`一返回該 值。 此值是[CALLBACK_CODE](callback-code-enum.md)枚舉的成員。 |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x0000003) | 指定的 Windows (ETW) 追蹤的輸入事件追蹤無效。 |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x0000004) | 指定的輸出 ETW 追蹤無效。 |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x0000005) | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)結構未正確初始化。 |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x0000006) | [RELOG_CALLBACKS](relog-callbacks-struct.md)結構未正確初始化。 |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x0000007) | 無法打開輸入 ETW 追蹤。 |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x0000008) | 處理輸入 ETW 跟蹤時發生錯誤。 |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x0000009) | 嘗試啟動重新登錄作業階段時出錯。 |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | 輸入 ETW 跟蹤缺少重要事件。 |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x000000B) | 您正在不受支援的 Windows 版本上使用 C++生成見解。 |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x000000C) | 提供的會話名稱無效。 |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x000000D) | 此操作需要管理員許可權。 |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | 生成 GUID 時出錯。 |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | 嘗試確定暫存目錄路徑時出錯。 |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x0000010) | 嘗試為正在啟動的跟蹤工作階段創建臨時目錄時出錯。 |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | 嘗試啟動系統追蹤時出錯。 |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | 嘗試啟動 MSVC 跟蹤時出錯。 |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | 嘗試停止 MSVC 跟蹤時出錯。 |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | 嘗試啟動系統追蹤時出錯。 |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | 跟蹤已停止,但找不到跟蹤會話的臨時目錄。 |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | 找不到已停止的 MSVC 追蹤的追蹤檔。 |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | 使用內核跟蹤控制件合併追蹤時出錯。 |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | 發生未知的錯誤。 |

::: moniker-end
