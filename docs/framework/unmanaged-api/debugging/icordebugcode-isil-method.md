---
title: ICorDebugCode::IsIL 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: 77e55c4c3644ac4bd76f5c92152f4ee86cf5fa9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125559"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL 메서드

이 "ICorDebugCode"가 MSIL (Microsoft 중간 언어)로 컴파일된 코드를 나타내는지 여부를 나타내는 값을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>매개 변수

`pbIL`  
[out]이 `ICorDebugCode` MSIL로 컴파일된 코드를 나타내는 경우 `true` 합니다. 그렇지 않으면 `false`합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:** [시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.

**헤더:** CorDebug.idl, CorDebug.h

**라이브러리:** CorGuids.lib

**.NET Framework 버전:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
