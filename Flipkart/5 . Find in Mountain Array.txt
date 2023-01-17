class Solution {
public:
    int binarySearchL(MountainArray &mountainArr,int s,int e,int target){
        while(s<=e){
            int mid=s+(e-s)/2;
            if(mountainArr.get(mid)==target) 
                return mid;
           else if(mountainArr.get(mid)<target) //Moving Forward Ascending Array
                s=mid+1;
            else
                e=mid-1;
        }
        return -1;
    }
    int binarySearchR(MountainArray &mountainArr,int s,int e,int target){
        while(s<=e){
            int mid=s+(e-s)/2;
            if(mountainArr.get(mid)==target)
                return mid;
            else if(mountainArr.get(mid)>target) //Moving Forward Descending Array
                s=mid+1;
            else
                e=mid-1;
        }
        return -1;
    }
    int findInMountainArray(int target, MountainArray &mountainArr) {
        int n=mountainArr.length();
        int s=0,e=n-1;
        int peakEle;
        while(s<e){ // Finding Peak Element
            int mid=s+(e-s)/2;
            if(mountainArr.get(mid+1)>mountainArr.get(mid)){
                s=mid+1;
                peakEle=mid+1;
            }
            else
                e=mid;
        }
        int left = binarySearchL(mountainArr,0,peakEle,target); // Towards Left of the array
        int right = binarySearchR(mountainArr,peakEle,n-1, target); // Towards Right of the array
        return left>=0? left:right; //If target is present on the left return it otherwise the index at right
				//If not present we will return -1 as answer
    }
};