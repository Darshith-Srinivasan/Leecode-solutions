class Solution {
    public int repeatedStringMatch(String a, String b) {
        StringBuilder repeated = new StringBuilder(a);
        int count = 1;

        // Repeat `a` until it's at least as long as `b`
        while (repeated.length() < b.length()) {
            repeated.append(a);
            count++;
        }

        // Check if b is a substring of the current repeated string
        if (isSubstringZ(b, repeated.toString())) {
            return count;
        }

        // Try one more repeat to cover overlap cases
        repeated.append(a);
        if (isSubstringZ(b, repeated.toString())) {
            return count + 1;
        }

        return -1;
    }

    // Helper to check substring using Z-Algorithm
    private boolean isSubstringZ(String pattern, String text) {
        String concat = pattern + "#" + text;
        int[] z = computeZ(concat);
        int patternLen = pattern.length();

        for (int zVal : z) {
            if (zVal == patternLen) {
                return true;
            }
        }
        return false;
    }

    // Z-Algorithm implementation
    private int[] computeZ(String concat) {
        int n = concat.length();
        int[] z = new int[n];
        int l = 0, r = 0;

        for (int i = 1; i < n; i++) {
            if (i > r) {
                l = r = i;
                while (r < n && concat.charAt(r - l) == concat.charAt(r)) {
                    r++;
                }
                z[i] = r - l;
                r--;
            } else {
                int k = i - l;
                if (z[k] < r - i + 1) {
                    z[i] = z[k];
                } else {
                    l = i;
                    while (r < n && concat.charAt(r - l) == concat.charAt(r)) {
                        r++;
                    }
                    z[i] = r - l;
                    r--;
                }
            }
        }
        return z;
    }
}
