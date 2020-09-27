# codeitgogo

#include <iostream>
#include <set>
#include <unordered_map>
#include <map>
#include <vector>

#include <iostream>       // std::cout
#include <string>         // std::string

//#include <multiset>


using namespace std;


int main(){
	// the number of people
	int numPPL;
	// the number of seats
	int numSeat;
	// the required distance
	int dist;
	
	numPPL = 3;
	numSeat = 8;
	dist = 1;
	
        vector<vector<int>> DP(numPPL + 1, vector<int>(numSeat + 1, 0));
	for(int i = 0; i <= numSeat; i++){
		DP[1][i] = i;
	}
	
	for(int i = 2; i <= numPPL; i++){
		for(int j = 1; j <= numSeat; j++){
			DP[i][j] += DP[i][j - 1];
			if(j >= dist + 1){
				DP[i][j] += DP[i - 1][j - dist - 1];
			}
		}
	}
	
	cout<<DP[numPPL][numSeat]<<endl;
	
	return 0;
}
