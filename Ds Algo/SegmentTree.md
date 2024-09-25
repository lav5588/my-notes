
<a href = "./SegmentTree-Video-1.pdf">pdf Notes 1</a>
<a href = "./Segment Tree-Video-2.pdf">pdf Notes 2</a>
<a href = "./Segment Tree - Video - 3.pdf">pdf Notes 3</a>
<a href = "./Segment Tree - Video - 4.pdf">pdf Notes 4</a>

**Intution:-**

The provided C++ code implements a Segment Tree for efficient range sum queries and updates. It initializes the tree using the input data and allows querying the sum of elements within a specified range. The `buildTree` function constructs the tree recursively, while the `query` function retrieves sums by handling overlapping intervals. The `update` function enables modification of specific values in the original array, automatically adjusting the segment tree accordingly. 

```cpp
class SegmentTree {
public:
    SegmentTree(const vector<int>& inputData) {
        dataSize = inputData.size();
        segmentTree.resize(4 * dataSize); // Allocate space for the segment tree
        buildTree(inputData, 0, 0, dataSize - 1);
    }

    // Build the segment tree from the input data
    void buildTree(const vector<int>& inputData, int currentNode, int leftIndex, int rightIndex) {
        if (leftIndex == rightIndex) {
            // Leaf node will hold a single element from the input data
            segmentTree[currentNode] = inputData[leftIndex];
        } else {
            int midIndex = (leftIndex + rightIndex) / 2;
            // Recursively build the left and right subtrees
            buildTree(inputData, 2 * currentNode + 1, leftIndex, midIndex);
            buildTree(inputData, 2 * currentNode + 2, midIndex + 1, rightIndex);
            // Internal node will hold the sum of the two children
            segmentTree[currentNode] = segmentTree[2 * currentNode + 1] + segmentTree[2 * currentNode + 2];
        }
    }

    // Query the sum in the range [queryLeft, queryRight]
    int query(int queryLeft, int queryRight) {
        return query(0, 0, dataSize - 1, queryLeft, queryRight);
    }

    // Helper function to perform the range sum query
    int query(int currentNode, int leftIndex, int rightIndex, int queryLeft, int queryRight) {
        if (queryRight < leftIndex || rightIndex < queryLeft) {
            // Range represented by the node is completely outside the query range
            return 0; // Return 0 for out-of-bounds, since we are summing
        }
        if (queryLeft <= leftIndex && rightIndex <= queryRight) {
            // Range represented by the node is completely inside the query range
            return segmentTree[currentNode];
        }
        // Range represented by the node is partially inside and partially outside
        int midIndex = (leftIndex + rightIndex) / 2;
        int leftSum = query(2 * currentNode + 1, leftIndex, midIndex, queryLeft, queryRight);
        int rightSum = query(2 * currentNode + 2, midIndex + 1, rightIndex, queryLeft, queryRight);
        return leftSum + rightSum; // Return the total sum from both halves
    }

    // Update the value at a specific index
    void update(int indexToUpdate, int newValue) {
        update(0, 0, dataSize - 1, indexToUpdate, newValue);
    }

    // Helper function to perform the update
    void update(int currentNode, int leftIndex, int rightIndex, int indexToUpdate, int newValue) {
        if (leftIndex == rightIndex) {
            // Leaf node
            segmentTree[currentNode] = newValue;
        } else {
            int midIndex = (leftIndex + rightIndex) / 2;
            if (leftIndex <= indexToUpdate && indexToUpdate <= midIndex) {
                // If the index to update is in the left child, recurse on the left child
                update(2 * currentNode + 1, leftIndex, midIndex, indexToUpdate, newValue);
            } else {
                // If the index to update is in the right child, recurse on the right child
                update(2 * currentNode + 2, midIndex + 1, rightIndex, indexToUpdate, newValue);
            }
            // Internal node will hold the updated sum of the two children
            segmentTree[currentNode] = segmentTree[2 * currentNode + 1] + segmentTree[2 * currentNode + 2];
        }
    }

private:
    vector<int> segmentTree; // The segment tree data structure
    int dataSize; // Size of the original input data
};


```