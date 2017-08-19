Description:

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.



>For example, given array S = {-1 2 1 -4}, and target = 1.
he sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

Solution:

此题可基于 Three Sum 题的思路来写

```java
public int threeSumClosest(int[] nums, int target) {
    	Arrays.sort(nums);  // 从小到大排序
    	
        int res =  nums[0] + nums[1] + nums[2];    	// init res 作为三者之和的默认值
        int min = Math.abs(target -res);			// init min 目标值与三者之和的差的绝对值
        
        for ( int i = 0; i < nums.length - 2; i++){
        	if( i > 0 && nums[i] == nums[i-1]){
        		continue;
        	}
        	
        	int j = i + 1, k = nums.length - 1;
            
        	while( j < k ){
        		if( nums[i] + nums[j] + nums[k] == target){ // 存在res == target 则返回该target
        			System.out.println("==");
        			return target;
        		} else if (nums[i] + nums[j] + nums[k] > target){   // res > target 
        			if( (nums[i] + nums[j] + nums[k] - target) < min ){
        				min = Math.abs(nums[i] + nums[j] + nums[k] - target);
        				res = nums[i] + nums[j] + nums[k] ;
        			}
        			
        			k--;
        		} else if (nums[i] + nums[j] + nums[k] < target){  // res < target 
        			if( (target - (nums[i] + nums[j] + nums[k]) ) < min ){
        				min = Math.abs(target - (nums[i] + nums[j] + nums[k]));
        				res = nums[i] + nums[j] + nums[k] ;
        			}
        			
        			j++;
        		}
        		
        	}
        }
        return res;
    }	
```