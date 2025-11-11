algorithm 
Algorithm Merge(A, B)
Begin
    i ← 0
    j ← 0
    C ← empty list

    while i < length(A) and j < length(B) do
        if A[i] ≤ B[j] then
            C.append(A[i])
            i ← i + 1
        else
            C.append(B[j])
            j ← j + 1
        end if
    end while

    while i < length(A) do
        C.append(A[i])
        i ← i + 1
    end while

    while j < length(B) do
        C.append(B[j])
        j ← j + 1
    end while

    return C
End
