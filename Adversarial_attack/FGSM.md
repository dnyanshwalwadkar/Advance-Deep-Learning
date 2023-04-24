The Fast Gradient Sign Method (FGSM) is an adversarial attack method that crafts an adversarial example by adding small perturbations to the input image in the direction of the gradient of the loss function with respect to the input image. The goal is to find the smallest possible perturbation that can cause the model to misclassify the input image.

Mathematically, FGSM can be described as follows:

Given an input image x, a model f, and the target label y, calculate the loss function L:


L(x, y) = Loss(f(x), y)
f(x) represents the output of the model for input x, and Loss is the loss function (e.g., cross-entropy loss) used to measure the difference between the model's output and the target label y.

Calculate the gradient of the loss function with respect to the input image:


grad_x = ∇x L(x, y)
grad_x represents the gradient of the loss function L with respect to the input image x. This gradient tells us how the loss function changes as we change the input image x.

Compute the adversarial example by adding a small perturbation in the direction of the gradient of the loss function:


x_adv = x + ε * sign(grad_x)
x_adv represents the adversarial example, ε is a small constant (controlling the strength of the perturbation), and sign is the element-wise sign function that returns the sign of the gradient (i.e., +1 for positive elements, -1 for negative elements, and 0 for zero elements).

The FGSM attack works by exploiting the linearity of the model. By adding a small perturbation in the direction of the gradient, we can "push" the model's output towards the decision boundary, potentially causing it to cross the boundary and result in a misclassification. The key idea is that the model is highly sensitive to small perturbations in the input space due to its linear nature.

In our example, we are applying the FGSM attack to a Convolutional Neural Network (CNN) trained on the MNIST dataset. The steps involved in the attack are:

Feed the input image x to the model and compute the initial prediction.

Calculate the loss between the predicted output and the target label y.

Compute the gradient of the loss with respect to the input image x.

Create a perturbed image x_adv by adding a small perturbation (controlled by ε) in the direction of the gradient of the loss function.

Feed the perturbed image x_adv to the model and compute the final prediction.

Compare the initial and final predictions. If they are different, the attack was successful, and the model was fooled by the adversarial example.

The strength of the perturbation is controlled by the ε parameter. A larger ε value results in a stronger perturbation and a higher likelihood of fooling the model. However, a larger perturbation also makes the adversarial example more noticeable and less realistic. The goal is to find the smallest possible perturbation that can still cause the model to misclassify the input image.