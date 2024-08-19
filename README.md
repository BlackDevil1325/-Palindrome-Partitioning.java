# -Palindrome-Partitioning.java
class Solution {
    public boolean isPal(int left,int right,String str){
        while(left<=right){
            if(str.charAt(left) != str.charAt(right)) return false;
            left++;right--;
        }
        return true;
    }
    public void palindromePart(int ind,String s,List<String>ds,List<List<String>> ans){
        if(ind == s.length()){
            ans.add(new ArrayList<>(ds));
            return;
        }
        for(int i=ind;i<s.length(); i++){
            if(isPal(ind,i,s)){
                ds.add(s.substring(ind,i+1));
                palindromePart(i+1,s,ds,ans);
                ds.remove(ds.size()-1);
            }
        }
    }
    public List<List<String>> partition(String s) {
        List<List<String>> ans = new ArrayList<>();
        palindromePart(0,s,new ArrayList<>(),ans);
        return ans;
    }
}
