
```python

def winning_lottery(lottery_id, winning_id, k):
    
    centers = [] # tuple of index in lottery_id, index in winning_id where they match
    for ind1, char1 in enumerate(lottery_id):
        for ind2,char2 in enumerate(winning_id):
            if char1 == char2:
                centers.append([ind1,ind2])
    print(centers)
    
    def gen_diff_arr(lot_ind, win_ind):
        diff_arr = [0]
        left_lot = lot_ind - 1
        left_win = win_ind - 1
        while left_lot >= 0:
            if left_win >= 0:
                diff_arr.insert(0, abs(ord(lottery_id[left_lot]) - ord(winning_id[left_win])))
                left_win -= 1
            else:
                diff_arr.insert(0, -1)
            left_lot -= 1
        right_lot = lot_ind + 1
        right_win = win_ind + 1
        while right_lot < len(lottery_id):
            if right_win < len(winning_id):
                diff_arr.append(abs(ord(lottery_id[right_lot]) - ord(winning_id[right_win])))
                right_win += 1
            else:
                diff_arr.append(-1)
            right_lot += 1
        print(lot_ind, lottery_id[lot_ind], win_ind, winning_id[win_ind], lottery_id, winning_id, diff_arr)
        return diff_arr
    
    diff_arrs = [gen_diff_arr(lot_ind, win_ind) for lot_ind, win_ind in centers]
    print(diff_arrs)
    max_len = 0
    for i in range(len(centers)):
        start_ind = centers[i][0]
        diff_arr = diff_arrs[i]
        l,r = start_ind - 1, start_ind + 1
        ops_used = 0
        while l >= 0 and diff_arr[l] != -1 and r < len(lottery_id) and diff_arr[r] != -1:
            if diff_arr[l] <= diff_arr[r]:
                ops_used += diff_arr[l]
                if ops_used > k:
                    ops_used -= diff_arr[l]
                    break
                l -= 1   
            else:
                ops_used += diff_arr[r]
                if ops_used > k:
                    ops_used -= diff_arr[r]
                    break
                r += 1
        
        while l >= 0 and diff_arr[l] != -1:
            ops_used += diff_arr[l]
            if ops_used > k:
                ops_used -= diff_arr[l]
                break
            l -= 1
        
        while r < len(lottery_id) and diff_arr[r] != -1:
            ops_used += diff_arr[r]
            if ops_used > k:
                ops_used -= diff_arr[r]
                break
            r += 1
        if l < 0:
            l = 0
        if r >= len(lottery_id):
            r = len(lottery_id) - 1
        print(diff_arr, l, r, r-l)
        
        max_len = max(max_len, r - l)
    print(max_len)
    return max_len
        
            
            
        

# winning_lottery("abcdef", "ghifac", 12)
winning_lottery("bfghcd", "abcd", 13)
# winning_lottery("abc", "def", 12)
    

```