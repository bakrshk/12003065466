# 12003065466
public class BinarySearchTree extends BinaryTree

{

 

    public void insert (int item)

    {

        BinaryTreeNode current;             //reference variable to traverse tree

        BinaryTreeNode trailCurrent = null; //reference variable behind current

        BinaryTreeNode newNode;             //reference variable to create node

 

        newNode = new BinaryTreeNode();


        newNode.info = item;

        newNode.lLink = null;

        newNode.rLink = null;

 

        if (root == null)

            root = newNode;

        else

        {

            current = root;

            while (current != null)

            {

                trailCurrent = current;

                if (current.info == item)

                {

                    System.err.print("Item is already in the list. No duplicates allowed.");

                    return;

                }

                else

                {

                    if (current.info > item)

                        current = current.lLink;

                    else
                        current = current.rLink;

                }

            }

 

            if (trailCurrent.info > item)

                trailCurrent.lLink = newNode;

            else

                trailCurrent.rLink = newNode;

 

        }

    }

 

    //Finds the node to be deleted and passes it to DeleteNode

    public void delete (int item)

    {

        BinaryTreeNode current;         //reference variable to traverse tree

        BinaryTreeNode trailCurrent;    //reference variable behind current

 
        boolean found = false;

 

        if (root == null)

            System.err.println ("Cannot delete from an empty tree.");

        else

        {

            current = root;

            trailCurrent = root;

 

            while (current != null && !found)

            {

                if (current.info == item)

                    found = true;

                else

                {

                    trailCurrent = current;

 

                    if (current.info > item)

                        current = current.lLink;

                    else

                        current = current.rLink;

                }

            }

 

            if (current == null)

                System.out.println ("Delete item is not in the list.");

            else

                if (found)

                {

                    if (current == root)

                        root = deleteNode(root);

                    else

                        if (trailCurrent.info > item)

                            trailCurrent.lLink = deleteNode(trailCurrent.lLink);

                        else

                            trailCurrent.rLink = deleteNode(trailCurrent.rLink);

                }

        }

    }

 

    //Removes node from tree

    private BinaryTreeNode deleteNode (BinaryTreeNode n)

    {

        BinaryTreeNode current;         //reference variable to traverse tree

        BinaryTreeNode trailCurrent;    //reference variable behind current

 

        if (n == null)

            System.err.println ("Error:  Node to be deleted is null.");

        else if (n.lLink == null && n.rLink == null)

            n = null;

        else if (n.lLink == null)

            n = n.rLink;

        else if (n.rLink == null)

            n = n.lLink;

        else

        {

            current = n.lLink;

            trailCurrent = null;
 
            while (current.rLink != null)
            {
                trailCurrent = current;
                current = current.rLink;
            }
 
            n.info = current.info;
 
            if (trailCurrent == null)
               n.lLink = current.lLink;
            else
                trailCurrent.rLink = current.lLink;
        }
 
        return n;

    }

}
