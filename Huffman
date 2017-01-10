#include <iostream>
#include <iomanip>
#include <list>
#include <algorithm>
#include <fstream>
#include <set>
#include <vector>
#include <utility>
#include <map>
#include <math.h>
#include <iostream>
#include <string>
#include <cstddef>
#include <bitset>
#include <iostream>
#include <sstream>
#include <string>
//#include <forward_list>
#include <math.h>
#include <iostream>
#include <string>
#include <cctype>
#include <stack>
#include<stdio.h>
#include<stdio.h>
#include <stdio.h>
using namespace std;
typedef vector<int > vi;
typedef vector<char > vc;
typedef vector<string > vs;
typedef vector<vector<int> > vvi;
typedef vector<vector<string> > vvs;
#include <string.h>

#include <queue>
#include <iostream>


struct Node {
    Node * left;
    Node * Right;
    char c;
};

//typedef struct Node Node;

struct Node_Frequency{
    Node * node;
    int frequency;

    bool operator<(const Node_Frequency& other) const {
        return frequency > other.frequency;
    }
};

void printTree(Node* node) {
    if (node == NULL) return;

    cout << node->c << " ";
    printTree(node->left);
    printTree(node->Right);
}

typedef struct Node_Frequency Node_Frequency;

map <char , string> HuffmanCode;
void Recursive_Traverse(Node * Temp , char ch, string HuffmanCodeS){
    if(Temp->left == NULL || Temp->Right == NULL) {
        HuffmanCodeS+= ch;
//        cout << Temp->c << " " << HuffmanCodeS<<endl;
        HuffmanCode[Temp->c] = HuffmanCodeS;
        return ;
    }
    else{
        HuffmanCodeS += ch;
        //cout << Temp->c << " " << HuffmanCodeS<<endl;
        Recursive_Traverse(Temp->left, '0' , HuffmanCodeS);
        Recursive_Traverse(Temp->Right, '1' , HuffmanCodeS);
    }
}

int main(){
    stringstream SASCII ;
    string ASCII ;
    cin >> ASCII;
    SASCII << ASCII;
    int Each_Char = 0;
    vector<char> letter;
//    vector<pair<char , int>> Vector_Frequency;
    char c ;
    map<char , int> Char_Frequency ;
    int i = 0;
    while (SASCII >> c) {
        i++;
        Each_Char += pow( 2 , (8-i)) * (c - 48);
        if(i == 8) {
            i = 0;
            letter.push_back((char) Each_Char);
            Char_Frequency[(char) Each_Char] ++;
            Each_Char = 0;
        }
    }
    //for (vc :: iterator it1 = letter.begin() ; it1 != letter.end();  it1++)
        //cout << (*it1) ;
   // cout << endl;
    priority_queue<Node_Frequency> minHeap;
    for (map<char , int>:: iterator iterator1 = Char_Frequency.begin(); iterator1!=Char_Frequency.end() ; iterator1++ ){
        Node *temp = new Node ;
        temp->left = NULL;
        temp->Right = NULL;
        temp->c = (*iterator1).first;
        Node_Frequency To_temp;
        To_temp.node = temp;
        To_temp.frequency = (*iterator1).second;
        minHeap.push(To_temp);
    }


    Node* TmpRoot;
    while (minHeap.size() !=1) {
//        cout <<endl;
//        cout << minHeap.top().frequency ;
        Node_Frequency TmpLeft , TmpRight ;
        TmpLeft = minHeap.top();
        minHeap.pop();
        TmpRight = minHeap.top();
        minHeap.pop();
        //printTree(TmpRight.node); cout << endl;
        //printTree(TmpLeft.node); cout << endl;
        TmpRoot = new Node();
        TmpRoot->Right = TmpRight.node;
        TmpRoot->left = TmpLeft.node;
  //      printTree(TmpRoot); cout << endl;
        Node_Frequency *TmpFrequencyRoot = new Node_Frequency();
        TmpFrequencyRoot->node = TmpRoot;
        TmpFrequencyRoot->frequency = TmpLeft.frequency + TmpRight.frequency;
        minHeap.push(*TmpFrequencyRoot);
    }
    string HuffmanCodes ;
    Recursive_Traverse(TmpRoot->left , '0',HuffmanCodes );
    Recursive_Traverse(TmpRoot->Right, '1' , HuffmanCodes);
    for (map < char , string > :: iterator iterator2 = HuffmanCode.begin() ; iterator2 != HuffmanCode.end() ; iterator2++) {
        cout << (*iterator2).first << "  " << (*iterator2).second<<endl  ;
    }
    for (int j = 0; j < letter.size(); ++j) {
        cout<<HuffmanCode[letter[j]];
    }
    cout <<endl;


}
//0100000101110110010000010111011000110011
//010000010111011001000001011101100011001101000001011101100100000101110110001100110011001100110011001100110011001100110011001100110011001100110011001100110011001100110011001100110011001100111100001111000011110000111100001111000011110000111100001111000011110000111100001111000011110000111100001111000011110000111100  -->  AvAv3AvAv33333333333333<<<<<<<<<<<<<<<<
//0110100001100101011011000110110001101111001000000110110101111001001000000110011001110010011010010110010101101110011001000110010001100100011001000110010001100100011011000110100101101100011010010010000001101000011011110111101001100001011010110010000001100111011011110110111001100011011010000110100101101011011001010010000001110010011000010110011001110100001000000110000101100010001000000110001001101111011010110110100001101111011100100110010100100000011011110110011001110100011000010110010000100000011101000110111101101111001000000110100001101111011110100110000101101011
